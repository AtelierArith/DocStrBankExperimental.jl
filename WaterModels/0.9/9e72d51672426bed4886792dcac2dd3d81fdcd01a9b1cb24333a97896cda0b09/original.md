```
constraint_pipe_flow(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

Adds constraints that limit the amount of flow traveling in the positive (forward) and negative (reverse) directions. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `a` is the index of the pipe, `q_max_reverse` is the *maximum* (negative) amount of flow when flow is traveling in the negative direction (which corresponds to the *minimum* magnitude of flow when traveling in the negative direction), and `q_min_forward` is the *minimum* (positive) amount of flow when flow is traveling in the positive (forward) direction. Note that, naively, `q_max_reverse` and `q_min_forward` could both be assumed as zero, but the introduction of these constants allows for strengthening of flow direction variable bounds *based on the binary flow direction variables* used here.
