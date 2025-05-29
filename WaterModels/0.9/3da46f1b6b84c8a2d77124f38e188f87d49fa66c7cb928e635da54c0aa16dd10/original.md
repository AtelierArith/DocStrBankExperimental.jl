```
variable_valve_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Creates binary variables for valves in the network at subnetwork (or time) index `nw`, i.e., `z_valve[a]` for `a` in `valve`. Here, one denotes that the valve is open and zero denotes that the valve is closed.
