```
constraint_on_off_des_pipe_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int
)
```

Adds constraints that limit the (design pipe-specific) head differences across a design pipe based on the construction status of the design pipe (i.e., there is zero head loss across the design pipe if it is not constructed). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the design pipe, `node_fr` is the index of the tail node of the pipe, and `node_to` is the index of the head node of the pipe.
