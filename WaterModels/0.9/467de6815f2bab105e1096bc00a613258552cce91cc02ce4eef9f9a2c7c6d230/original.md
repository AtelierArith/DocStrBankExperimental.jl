```
constraint_short_pipe_flow(
    wm::AbstractWaterModel,
    a::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_short_pipe_flow`](@ref) constraints that limit the volumetric flow rate across a short pipe. Here, `wm` is the WaterModels object, `a` is the index of the short pipe for which flow will be limited, and `nw` is the subnetwork (or time) index that is considered.
