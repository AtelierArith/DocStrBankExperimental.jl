```
variable_reservoir_flow(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded outgoing volumetric flow rate variables for reservoirs in the network at subnetwork (or time) index `nw`, i.e., `q_reservoir[i]` for `i` in `reservoir`. Note that these variables are always nonnegative, since for each reservoir, there will never be incoming flow.
