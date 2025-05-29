```
constraint_on_off_pump_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_flow`](@ref) constraints, which restrict the amount of flow transported through a pump based on its operating status. Here, `wm` is the WaterModels object, `a` is the index of the pump, and `nw` is the index of a subnetwork within a multinetwork.
