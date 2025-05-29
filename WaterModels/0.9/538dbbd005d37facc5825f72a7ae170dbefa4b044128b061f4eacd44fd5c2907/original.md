```
variable_pump_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Creates binary variables for pumps in the network at subnetwork (or time) index `nw`, i.e., `z_pump[a]` for `a` in `pump`, where one denotes that the pump is currently operating (i.e., on), and zero indicates that the pump is not operating (i.e., off).
