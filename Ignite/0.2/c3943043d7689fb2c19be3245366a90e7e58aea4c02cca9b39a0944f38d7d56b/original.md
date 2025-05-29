```julia
struct OrEvent{E1<:Ignite.AbstractEvent, E2<:Ignite.AbstractEvent} <: Ignite.AbstractEvent
```

`OrEvent(event1, event2)` wraps two events and triggers if either of the wrapped events are triggered by a firing event firing.

`OrEvent`s can be constructed via the `|` operator: `event1 | event2`.

Fields: 

  * `event1::Ignite.AbstractEvent`: The first wrapped event that will be checked if it should be fired.
  * `event2::Ignite.AbstractEvent`: The second wrapped event that will be checked if it should be fired.
