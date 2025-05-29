```
constraint_on_off_valve_flow(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

Adds constraints that limit the amount of flow along a valve based on the operating status of the valve (i.e., there is bounded flow if the valve is active and zero flow if the valve is inactive). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the valve, `q_max_reverse` is the *maximum* (negative) amount of flow when flow is traveling in the negative direction (which corresponds to the *minimum* magnitude of flow when traveling in the negative direction), and `q_min_forward` is the *minimum* (positive) amount of flow when flow is traveling in the positive (forward) direction.
