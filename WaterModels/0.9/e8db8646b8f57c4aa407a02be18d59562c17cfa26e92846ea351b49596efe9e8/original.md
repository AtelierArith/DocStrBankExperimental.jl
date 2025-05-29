```
variable_flow(
    wm::AbstractNCDModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded direction-based flow variables for all node-connecting components (e.g., pipes, pumps) in the network at subnetwork (or time) index `nw`, e.g., `qp_pipe[a]` and `qn_pipe[a]` for `a` in `pipe` (i.e., positively-directed and negatively-directed flow through the pipe). Also creates JuMP expressions for direction-valued flow, e.g., `q_pipe[a] = qp_pipe[a] - qn_pipe[a]` for `a` in `pipe`. Also creates binary flow direction variables, e.g., `y_pipe[a]` for `a` in `pipe`, where one indicates flow traveling from `node_fr` (tail of the arc) to `node_to` (head of the arc). Also creates direction-based head difference variables for pipes and design pipes in the network, e.g., `dhp_pipe[a]` and `dhn_pipe[a]` for `a` in `pipe`. Used for flow direction-based network model formulations only.
