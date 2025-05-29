```
constraint_pipe_head_loss(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_pipe_head_loss`](@ref) constraints that model head loss relationships along a pipe. Here, `wm` is the WaterModels object, `a` is the index of the pipe, and `nw` is the subnetwork (or time) index that is considered.
