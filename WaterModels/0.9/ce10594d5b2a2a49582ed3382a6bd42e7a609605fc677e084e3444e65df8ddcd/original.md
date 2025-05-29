```
constraint_on_off_des_pipe_head(
    wm::AbstractNCDModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

Adds constraints that limit head differences (losses) in the positive (forward) and negative (reverse) directions for a design pipe. Also limits losses based on the construction status of the design pipe, i.e., restricting both losses to zero if a design pipe is not constructed. Here, `wm` is the WaterModels object, `n` is the index of a subnetwork within a multinetwork, `a` is the index of the design pipe, `node_fr` is the index of the tail node of the arc that models the design pipe, and `node_to` is the index of the head node of the arc that models the design pipe.
