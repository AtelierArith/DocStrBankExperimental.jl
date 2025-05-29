```
variable_demand_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates unbounded volumetric flow rate demand variables for all *dispatchable* demands in the network at subnetwork (or time) index `nw`, i.e., `q_demand[i]` for `i` in `dispatchable_demand`.
