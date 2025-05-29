```
constraint_on_off_pump_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_head`](@ref) constraints, which disjunctively limit the head difference between nodes connected by the pump and, if operating, ensures the head difference between nodes is equal to the head gain, constrained by ([`constraint_on_off_pump_head_gain`](@ref). Here, `wm` is the WaterModels object, `a` is the index of the pump, and `nw` is the index of a subnetwork within a multinetwork.
