```
constraint_node_directionality(
    wm::AbstractWaterModel,
    i::Int;
    nw::Int=nw_id_default
)
```

Constraint template to add direction-based constraints ([`constraint_sink_directionality`](@ref), [`constraint_source_directionality`](@ref), or [`constraint_intermediate_directionality`](@ref)) when appropriate. Here, `wm` is the WaterModels object, `i` is the index of the node for which the constraints will be added, if applicable, and `nw` is the subnetwork (or time) index.
