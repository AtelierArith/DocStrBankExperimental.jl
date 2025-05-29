```
constraint_tank_volume(
    wm::AbstractWaterModel,
    i::Int,
    nw_1::Int,
    nw_2::Int
)
```

Constraint template to add [`constraint_tank_volume`](@ref) constraints that integrate the volume of a tank forward in time. Here, `wm` is the WaterModels object, `i` is the index of the tank for which the constraints will be added, `nw_1` is the first time index considered in the temporal integration, and `nw_2` is the adjacent (second) time index considered in the integration.
