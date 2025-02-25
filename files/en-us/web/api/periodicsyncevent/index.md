---
title: PeriodicSyncEvent
slug: Web/API/PeriodicSyncEvent
page-type: web-api-interface
tags:
  - API
  - Background Sync
  - Interface
  - Offline
  - PeriodicSyncEvent
  - Reference
  - ServiceWorker
  - Workers
browser-compat: api.PeriodicSyncEvent
---
{{DefaultAPISidebar("Periodic Background Sync")}}

The **`PeriodicSyncEvent`** interface of the {{domxref('Web Periodic Background Synchronization API')}} provides a way to run tasks in the service worker with network connectivity.

An instance of this event is passed to the {{domxref('ServiceWorkerGlobalScope.periodicsync_event', 'periodicsync')}} handler. This happens periodically, at an interval greater than or equal to that set in the {{domxref('PeriodicSyncManager.register()')}} method. Other implementation-specific factors such as the user's engagement with the site decide the actual interval.

{{InheritanceDiagram}}

## Constructor

- {{domxref("PeriodicSyncEvent.PeriodicSyncEvent()")}}
  - : Creates a new `PeriodicSyncEvent` object. This constructor is not typically used. The browser creates these objects itself and provides them to {{domxref('ServiceWorkerGlobalScope.periodicsync_event', 'onperiodicsync')}} callback.

## Properties

- {{domxref('PeriodicSyncEvent.tag')}} {{readonlyInline}}
  - : Returns the developer-defined identifier for this `PeriodicSyncEvent`. Multiple tags can be used by the web app to run different periodic tasks at different frequencies.

## Methods

Inherits methods from its parent {{domxref('ExtendableEvent')}}.

## Examples

The following example shows how to respond to a periodic sync event in the service worker.

```js
self.addEventListener('periodicsync', (event) => {
  if (event.tag == 'get-latest-news') {
    event.waitUntil(fetchAndCacheLatestNews());
  }
});
```

`fetchAndCacheLatestNews` is a developer defined function.

## Specifications

{{Specifications}}

## Browser compatibility

{{Compat}}

## See also

- [Richer offline experiences with the Periodic Background Sync API](https://web.dev/periodic-background-sync/)
- [A Periodic Background Sync demo app](https://webplatformapis.com/periodic_sync/periodicSync_improved.html)
