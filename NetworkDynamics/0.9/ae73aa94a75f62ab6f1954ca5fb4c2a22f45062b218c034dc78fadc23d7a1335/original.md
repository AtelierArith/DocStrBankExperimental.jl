```
DiscreteComponentCallback(condition, affect; kwargs...)
```

Connect a [`ComponentCondition`](@ref) and a [`ComponentAffect`)[@ref] to a discrete callback which can be attached to a component model using [`add_callback!`](@ref) or [`set_callback!`](@ref).

Note that the `condition` function returns a boolean value, as the discrete callback perform no rootfinding.

The `kwargs` will be forwarded to the `DiscreteCallback` when the component based callbacks are collected for the whole network using [`get_callbacks(::Network)`](@ref). [`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) for available options.
