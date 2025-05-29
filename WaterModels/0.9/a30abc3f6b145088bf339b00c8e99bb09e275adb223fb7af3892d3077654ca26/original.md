```
constraint_pump_switch_off(
    wm::AbstractWaterModel,
    a::Int,
    n_1::Int,
    n_2::Int,
    nws_inactive::Array{Int,1}
)
```

Adds a constraint that models the switching of a pump from *on* to *off* and constrains non-operation, if switched off, to remain off for at least some amount of time. Here, `wm` is the WaterModels object; `a` is the index of the pump; `n_1` is the first time index modeled by the constraint; `n_2` is the adjacent (next) time index modeled by the constraint, which permits limiting the change in pump status (i.e., from on to off); and `nws_inactive` are the subnetwork (time) indices where the pump must be constrained to off *if* the pump is indeed switched from on to off between time indices `n_1` and `n_2`.
