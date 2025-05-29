```julia
struct FilteredEvent{E<:Ignite.AbstractEvent, F} <: Ignite.AbstractEvent
```

`FilteredEvent(event::E, event_filter::F)` wraps an `event` and a `event_filter` function.

When a firing event `e` is fired, if `event_filter(engine, e)` returns `true` then the filtered event will be fired too.

Fields: 

  * `event::Ignite.AbstractEvent`: The wrapped event that will be fired if the filter function returns true when applied to a firing event.
  * `event_filter::Any`: The filter function `(::Engine, ::AbstractFiringEvent) -> Bool` returns `true` if the filtered event should be fired.
