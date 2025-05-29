```
constraint_on_off_regulator_flow(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_min_forward::Float64
)
```

Adds constraints that limit the amount of flow across a regulator based on the operating status of the regulator (i.e., there is bounded flow if the regulator is active and zero flow otherwise). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the regulator, and `q_min_forward` is the *minimum* (positive) amount of flow when the regulator is active.
