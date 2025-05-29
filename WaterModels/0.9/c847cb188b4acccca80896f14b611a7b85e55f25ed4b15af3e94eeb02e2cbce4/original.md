```
constraint_tank_volume(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

Constraint template to add [`constraint_tank_volume_fixed`](@ref) constraints when a tank is not dispatchable, usually at the first time index of a problem to fix the tank's initial volume. Here, `wm` is the WaterModels object, `i` is the index of the tank for which the constraints will be added, if applicable, and `nw` is the subnetwork (or time) index at which the volume will be fixed.
