```
PresetTimeComponentCallback(ts, affect; kwargs...)
```

Tirgger a [`ComponentAffect`](@ref) at given timesteps `ts` in discrete callback, which can be attached to a component model using [`add_callback!`](@ref) or [`set_callback!`](@ref).

The `kwargs` will be forwarded to the [`PresetTimeCallback`](@extref DiffEqCallbacks.PresetTimeCallback) when the component based callbacks are collected for the whole network using [`get_callbacks(::Network)`](@ref).

The `PresetTimeCallback` will take care of adding the timesteps to the solver, ensuring to exactly trigger at the correct times.
