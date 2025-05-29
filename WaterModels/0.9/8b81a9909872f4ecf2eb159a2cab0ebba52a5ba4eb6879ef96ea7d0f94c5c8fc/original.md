```
constraint_on_off_pump_power(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_pump_group`](@ref) constraints, which impose symmetry-breaking lexicographic sorting of pump activation statuses on groups of identical pumps operating in parallel along the same arc of the network. Here, `wm` is the WaterModels object, `k` is the index of the pump group, and `nw` is the index of a subnetwork within a multinetwork.
