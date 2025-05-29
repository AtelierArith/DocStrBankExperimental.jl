```
variable_regulator_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Creates binary variables for regulators in the network at subnetwork (or time) index `nw`, i.e., `z_regulator[a]` for `a` in `regulator`, where one denotes that the pressure reducing regulator is currently active and zero otherwise.
