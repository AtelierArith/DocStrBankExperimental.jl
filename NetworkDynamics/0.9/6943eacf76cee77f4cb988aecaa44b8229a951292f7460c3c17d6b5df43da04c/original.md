```
ContinousComponentCallback(condition, affect; kwargs...)
```

Connect a [`ComponentCondition`](@ref) and a [`ComponentAffect`)[@ref] to a continous callback which can be attached to a component model using [`add_callback!`](@ref) or [`set_callback!`](@ref).

The `kwargs` will be forwarded to the `VectorContinuousCallback` when the component based callbacks are collected for the whole network using `get_callbacks`. [`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) for available options.
