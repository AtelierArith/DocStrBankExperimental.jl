```
constraint_pipe_flow(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

Currently does nothing for models of type `AbstractNCModel`. Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pipe for which flow will be limited, `q_max_reverse` is the *maximum* (negative) amount of flow when flow is traveling in the negative direction (which corresponds to the *minimum* magnitude of flow when traveling in the negative direction), and `q_min_forward` is the *minimum* (positive) amount of flow when flow is traveling in the positive (forward) direction. For `AbstractNCModel` types, no constraints will be added, as in these formulation types, flow is not partitioned by direction, and flow bounds are instead imposed during variable instantiation in [`variable_flow`](@ref).
