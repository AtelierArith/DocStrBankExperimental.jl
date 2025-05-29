```
variable_flow(
    wm::AbstractPWLRDModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates flow-related variables linked to piecewise-linear, relaxation- and direction- (PWLRD-) based optimization models. First, creates direction-based flow variables for all node-connecting components (e.g., pipes) in the network at subnetwork (or time) index `nw`, e.g., `qp_pipe[a]` and `qn_pipe[a]` for `a` in `pipe`. Also creates JuMP expressions for direction-valued flow, e.g., `q_pipe[a] = qp_pipe[a] - qn_pipe[a]` for `a` in `pipe`. Also creates binary flow direction variables, e.g., `y_pipe[a]` for `a` in `pipe`, where one indicates flow traveling from `node_fr` (tail of the arc) to `node_to` (head of the arc). Also creates direction-based head difference variables for pipes and design pipes in the network, e.g., `dhp_pipe[a]` and `dhn_pipe[a]` for `a` in `pipe`. Then, creates continuous convex combination variables used to construct necessary piecewise-linear relaxations, e.g., `lambda_p_pipe[a]` and `lambda_n_pipe[a]` for `a` in `pipe`, where each is bounded between zero and one. Finally, creates binary convex combination variables used for piecewise-linear modeling of the relaxation constraints, e.g., `x_p_pipe[a]` and `x_n_pipe[a]` for `a` in `pipe`.
