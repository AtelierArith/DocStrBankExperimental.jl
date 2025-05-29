```
EventSource
```

Trait for actors that can publish events.

Manages subscriptions and dispatches events. You need to add a field `eventdispatcher::Addr` to your actor to use this trait.
