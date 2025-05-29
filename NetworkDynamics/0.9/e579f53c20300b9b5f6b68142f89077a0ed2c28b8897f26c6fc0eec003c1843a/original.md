```
VectorContinousComponentCallback(condition, affect, len; kwargs...)
```

Connect a [`ComponentCondition`](@ref) and a [`ComponentAffect`)[@ref] to a continous callback which can be attached to a component model using [`add_callback!`](@ref) or [`set_callback!`](@ref). This vector version allows for `condions` which have `len` output dimensions. The `affect` will be triggered with the additional `event_idx` argument to know in which dimension the zerocrossing was detected.

The `kwargs` will be forwarded to the `VectorContinuousCallback` when the component based callbacks are collected for the whole network using [`get_callbacks(::Network)`](@ref). [`DiffEq.jl docs`](https://docs.sciml.ai/DiffEqDocs/stable/features/callback_functions/) for available options.
