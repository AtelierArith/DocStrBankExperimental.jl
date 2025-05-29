```
constraint_on_off_pump_power(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_power`](@ref) constraints, which, if operating, model the pump's power according to certain assumptions. Here, `wm` is the WaterModels object, `a` is the index of the pump, and `nw` is the index of a subnetwork within a multinetwork.
