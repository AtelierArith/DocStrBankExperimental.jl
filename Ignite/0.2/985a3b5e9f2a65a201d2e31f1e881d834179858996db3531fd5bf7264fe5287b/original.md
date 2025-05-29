```julia
struct AndEvent{E1<:Ignite.AbstractEvent, E2<:Ignite.AbstractEvent} <: Ignite.AbstractEvent
```

`AndEvent(event1, event2)` wraps two events and triggers if and only if both wrapped events are triggered by the same firing event firing.

`AndEvent`s can be constructed via the `&` operator: `event1 & event2`.

Fields: 

  * `event1::Ignite.AbstractEvent`: The first wrapped event that will be considered for triggering.
  * `event2::Ignite.AbstractEvent`: The second wrapped event that will be considered for triggering.
