```
constraint_short_pipe_head(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
)
```

Adds a constraint that equates the head at the tail node of a short pipe with the head at the head node of the short pipe (i.e., since short pipes have no loss). Here, `wm` is the WaterModels object, `n` is the subnetwork (or time) index that is considered, `a` is the index of the short pipe, `node_fr` is the index of the tail node of the short pipe, and `node_to` is the index of the head node of the short pipe.
