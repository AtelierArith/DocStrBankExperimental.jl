```
constraint_des_pipe_flow(
    wm::AbstractWaterModel,
    k::Int,
    node_fr::Int,
    node_to::Int;
    nw::Int=nw_id_default,
    kwargs...,
)
```

Constraint template to add constraints that ensure flow variables for design pipes along an arc are equally directed (for direction-based formulations). Here, `wm` is the WaterModels object, `k` is the index of the arc that connects the two common nodes of each design pipe, `node_fr` is the index of the tail node of the arc that models each design pipe, `node_to` is the index of the head node of the arc that models each design pipe, `nw` is the index of a subnetwork within a multinetwork, and `des_pipes` is the vector of design pipe indices for design pipes that reside along the same arc `k`.
