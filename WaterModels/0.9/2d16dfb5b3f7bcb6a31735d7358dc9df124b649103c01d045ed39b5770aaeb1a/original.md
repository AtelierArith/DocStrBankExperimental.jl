```
constraint_des_pipe_flow(
    wm::AbstractNCModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

Currently does nothing for models of type `AbstractNCModel`. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `k` is the index of the arc that connects the two common nodes of each design pipe, `node_fr` is the index of the tail node of the arc that models each design pipe, `node_to` is the index of the head node of the arc that models each design pipe, and `des_pipes` is the vector of design pipes that reside along the same arc `k`. For `AbstractNCModel` types, no constraints will be added, as in these formulation types, flow is not partitioned by direction, and flow bounds are instead imposed during variable instantiation in [`variable_flow`](@ref).
