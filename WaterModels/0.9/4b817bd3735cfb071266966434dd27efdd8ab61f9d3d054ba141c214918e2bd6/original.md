```
variable_flow(
    wm::AbstractNCModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded flow variables for all node- connecting components (e.g., pipes, pumps) in the network at subnetwork (or time) index `nw`, e.g., `q_pipe[a]` for `a` in `pipe`, `q_pump[a]` for `a` in `pump`. Used for non-flow-direction-based network model formulations only.
