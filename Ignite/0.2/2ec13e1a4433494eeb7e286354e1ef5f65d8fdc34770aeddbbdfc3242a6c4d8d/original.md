```julia
add_event_handler!(
    handler!,
    engine::Ignite.Engine,
    event::Ignite.AbstractEvent,
    handler_args...
) -> Ignite.Engine

```

Add an event handler to an engine which is fired when `event` is triggered.

When fired, the event handler is called as `handler!(engine::Engine, handler_args...)`.
