```
add_event!(agent, model)
```

Generate a randomly chosen event for the `agent` and add it to the queue, based on the propensities and as described in [`EventQueueABM`](@ref).

```
add_event!(agent, event_idx, t::Real, model::EventQueueABM)
```

Add a new event to the queue to be triggered for `agent`, based on the index of the event (from the given `events` to the `model`). The event will trigger in `t` time *from* the current time of the `model`.
