```
variable_pump_switch_off(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Creates binary variables for pumps in the network at subnetwork (or time) index `nw`, i.e., `z_switch_off_pump[a]` for `a` in `pump`, where one denotes that the pump has been switched to the "off" status at the current subnetwork (or time) index, and zero indicates that the pump has had no status change.
