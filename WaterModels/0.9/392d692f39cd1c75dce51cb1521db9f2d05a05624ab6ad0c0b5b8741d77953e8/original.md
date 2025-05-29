```
constraint_on_off_valve_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_valve_flow`](@ref) constraints that limit the volumetric flow rate across a valve based on its operating status. Here, `wm` is the WaterModels object, `a` is the index of the valve for which flow will be limited, and `nw` is the subnetwork (or time) index that is considered.
