```julia
abstract type AbstractLoopEvent <: Ignite.AbstractFiringEvent
```

Abstract supertype for events fired during the normal execution of [`Ignite.run!`](@ref).

A default convenience constructor `(EVENT::Type{<:AbstractLoopEvent})(; kwargs...)` is provided to allow for easy filtering of `AbstractLoopEvent`s. For example, `EPOCH_COMPLETED(every = 3)` will build a [`FilteredEvent`](@ref) which is triggered every third epoch. See [`filter_event`](@ref) for allowed keywords.

By inheriting from `AbstractLoopEvent`, custom events will inherit these convenience constructors, too. If this is undesired, one can instead inherit from the supertype `AbstractFiringEvent`.
