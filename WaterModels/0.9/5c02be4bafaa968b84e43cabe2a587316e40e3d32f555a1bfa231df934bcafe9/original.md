```
constraint_des_pipe_selection(
    wm::AbstractWaterModel,
    n::Int,
    k::Int,
    node_fr::Int,
    node_to::Int,
    des_pipes::Array{Int,1}
)
```

Adds a constraint that ensures exactly one design pipe will be selected per arc that comprises one or more design pipe possibilities. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `k` is the index of the arc comprising multiple design pipes, `node_fr` and `node_to` are node indices that connect the arc, and `des_pipes` is the vector of design pipes that reside along the same arc `k`.
