```
function constraint_pump_switch_off(
    wm::AbstractWaterModel,
    a::Int,
    n_1::Int,
    n_2::Int;
    kwargs...
)
```

Constraint template to add [`constraint_pump_switch_off`](@ref) constraints, which model the switching of a pump from *on* to *off* and constrains non- operation, if switched off, to remain off for at least some minimum amount of time. Here, `wm` is the WaterModels object; `a` is the index of the pump; `n_1` is the first time index modeled by the constraint; `n_2` is the adjacent (next) time index modeled by the constraint, which permits limiting the change in pump status (i.e., from on to off).
