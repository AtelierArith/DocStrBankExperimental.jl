```
constraint_des_pipe_selection(
    wm::AbstractWaterModel,
    k::Int,
    node_fr::Int,
    node_to::Int;
    nw::Int=nw_id_default,
    kwargs...
)
```

Constraint template to add [`constraint_des_pipe_selection`](@ref) constraints that enforce the selection of only one design pipe to be constructed along a given arc. Here, `wm` is the WaterModels object, `k` is the index of the arc that connects the two common nodes of each design pipe, `node_fr` is the index of the tail node of the arc that models each design pipe, `node_to` is the index of the head node of the arc that models each design pipe, and `nw` is the index of a subnetwork within a multinetwork.
