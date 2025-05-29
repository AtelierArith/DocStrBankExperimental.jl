```
constraint_pump_switch_on(
    wm::AbstractWaterModel,
    a::Int,
    n_1::Int,
    n_2::Int,
    nws_active::Array{Int,1}
)
```

Adds a constraint that models the switching of a pump from *off* to *on* and constrains its operation, if switched on, to remain on for at least some amount of time. Here, `wm` is the WaterModels object; `a` is the index of the pump; `n_1` is the first time index modeled by the constraint; `n_2` is the adjacent (next) time index modeled by the constraint, which permits limiting the change in pump status (i.e., from off to on); and `nws_active` are the subnetwork (time) indices where the pump must be constrained to on *if* the pump is indeed switched from off to on between time indices `n_1` and `n_2`.
