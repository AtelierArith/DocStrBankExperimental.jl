```
constraint_on_off_pump_head_gain(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_head_gain`](@ref) constraints, which, if operating, limit the pump's head gain as a function of flow rate. Here, `wm` is the WaterModels object, `a` is the index of the pump, and `nw` is the index of a subnetwork within a multinetwork.
