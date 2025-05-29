```
constraint_pump_switch_on(
    wm::AbstractWaterModel,
    a::Int,
    n_1::Int,
    n_2::Int;
    kwargs...
)
```

Constraint template to add [`constraint_pump_switch_on`](@ref) constraints, which model the switching of a pump from *off* to *on* and constrains its operation, if switched on, to remain on for at least some minimum amount of time. Here, `wm` is the WaterModels object; `a` is the index of the pump; `n_1` is the first time index modeled by the constraint; and `n_2` is the adjacent (next) time index modeled by the constraint, which permits limiting the change in pump status (i.e., from off to on).
