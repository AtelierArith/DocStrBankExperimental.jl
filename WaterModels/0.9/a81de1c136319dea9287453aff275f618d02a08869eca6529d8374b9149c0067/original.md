```
variable_des_pipe_indicator(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    relax::Bool=false,
    report::Bool=true
)
```

Creates binary variables for design pipes in the network at subnetwork (or time) index `nw`, i.e., `z_des_pipe[a]` for `a` in `des_pipe`, where one denotes that the pipe has been selected within the design at the current subnetwork (or time) index, and zero indicates that the design pipe has had not been selected.
