```julia
abstract type AbstractFiringEvent <: Ignite.AbstractEvent
```

Abstract supertype for all events which can trigger event handlers via [`fire_event!`](@ref).
