```
variable_flow(
    wm::AbstractLAModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates flow-related variables related to linear approximation- (LA-) based optimization models. First, creates flow variables for all node-connecting components (e.g., pipes) in the network at subnetwork (or time) index `nw`, e.g., `q_pipe[a]` for `a` in `pipe`. Then, creates continuous convex combination variables used to construct necessary linear approximations, e.g., `lambda_pipe[a]` for `a` in `pipe`, where each is bounded between zero and one. Finally, creates binary convex combination variables used for piecewise-linear modeling of the approximating constraints, e.g., `x_pipe[a]` for `a` in `pipe`.
