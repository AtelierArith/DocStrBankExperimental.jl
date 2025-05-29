```julia
fire_event!(
    engine::Ignite.Engine,
    e::Ignite.AbstractFiringEvent
) -> Ignite.Engine

```

Execute all event handlers triggered by the firing event `e`.
