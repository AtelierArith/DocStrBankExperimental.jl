```
constraint_on_off_regulator_head(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_regulator_head`](@ref) constraints that limit and establish relationships among head variables based on the operating status of the regulator. Here, `wm` is the WaterModels object, `a` is the index of the regulator, and `nw` is the subnetwork (or time) index that is considered.
