```
constraint_on_off_pump_power_custom(
    wm::AbstractWaterModel,
    n::Int,
    a::Int,
    power_fixed::Float64,
    power_variable::Float64
)
```

Adds a constraint that expresses pump power as a linear expression of flow, where coefficients of this linear expression are given by `power_fixed` and `power_variable`. Here, `wm` is the WaterModels object, `n` is the index of the subnetwork within a multinetwork, `a` is the index of the pump, `power_fixed` is the amount of power consumed by the pump when it is active and transporting no flow (i.e., the point of intersection at zero flow on the vertical axis of a power-versus-flow curve), and `power_variable` is the amount of power consumed by the pump per unit flow.
