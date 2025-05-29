```
constraint_on_off_pump_flow(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    q_min_forward::Float64
)
```

Adds constraints that limit the amount of flow across a pump based on the operating status of the pump (i.e., there is unrestricted but bounded flow if the pump is active and zero flow otherwise). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pump, and `q_min_forward` is the *minimum* (positive) amount of flow when the pump is active. Here, `q_min_forward` could be interpreted as some minimum amount of flow recommended by the pump manufacturer to avoid pump overheating, or it may be some network- or optimization-based bound (e.g., a flow bound discovered via optimization-based bound tightening).
