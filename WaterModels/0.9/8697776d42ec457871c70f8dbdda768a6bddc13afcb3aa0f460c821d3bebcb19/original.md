```
constraint_on_off_des_pipe_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_on_off_des_pipe_flow`](@ref) constraints that limit the amount of flow traveling across a design pipe. Here, `wm` is the WaterModels object, `a` is the index of the design pipe, and `nw` is the index of a subnetwork within a multinetwork.
