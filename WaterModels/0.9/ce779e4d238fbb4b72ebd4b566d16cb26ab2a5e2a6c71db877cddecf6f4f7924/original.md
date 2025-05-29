```
variable_tank_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded volumetric flow rate variables for tanks in the network at subnetwork (or time) index `nw`, i.e., `q_tank[i]` for `i` in `tank`. Note that, unlike reservoirs, tanks can have inflow, represented as a negative quantity.
