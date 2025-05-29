```
constraint_pipe_head(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
)
```

Adds constraints that limit head losses (differences) in the positive (forward) and negative (reverse) flow directions. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `a` is the index of the pipe, `node_fr` is the index of the tail node of the arc that models the pipe, and `node_to` is the index of the head node of the arc that models the pipe.
