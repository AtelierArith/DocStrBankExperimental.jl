```
constraint_on_off_pump_power(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    q_min_forward::Float64
)
```

Adds constraints that model the pump's power consumption, if operating, as a quadratic function of flow rate. If the pump is inactive, the power is restricted to a value of zero. Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pump, and `q_min_forward` is the *minimum* (positive) amount of flow when the pump is active. Note only a quadratic approximation is used for `AbstractNCDModel`.
