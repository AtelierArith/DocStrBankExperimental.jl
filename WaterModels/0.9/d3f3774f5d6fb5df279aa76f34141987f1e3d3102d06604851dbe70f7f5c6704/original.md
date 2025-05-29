```
constraint_on_off_pump_power_best_efficiency(
    wm::AbstractWaterModel,
    n::Int,
    a::Int,
    density::Float64,
    gravity::Float64,
    q_min_forward::Float64
)
```

Adds a constraint that expresses pump power as a linear expression of flow, where coefficients of this linear expression are computed using an assumption that the pump will be operating at its best efficiency point. Here, `wm` is the WaterModels object, `n` is the index of the subnetwork within a multinetwork, `a` is the index of the pump, `density` is the density of water, `gravity` is acceleration due to gravity, and `q_min_forward` is the minimum amount of flow transported through the pump when it is active (and flow is directed forward).
