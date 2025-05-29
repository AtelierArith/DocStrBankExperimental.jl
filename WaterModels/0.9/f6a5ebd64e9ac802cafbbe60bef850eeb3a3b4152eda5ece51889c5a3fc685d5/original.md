```
constraint_pipe_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

Add constraints that limit the head difference (loss) along a pipe based on the lower and upper bounds of head variables at the nodes connecting that pipe. Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the pipe, `node_fr` is the index of the tail node of the pipe, and `node_to` is the index of the head node of the pipe.
