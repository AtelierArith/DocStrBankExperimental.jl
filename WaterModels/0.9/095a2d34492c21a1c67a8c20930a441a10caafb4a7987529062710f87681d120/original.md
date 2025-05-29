```
constraint_pipe_head_loss(
    wm::AbstractNCModel,
    n::Int,
    a::Int,
    node_fr::Int,
    node_to::Int,
    exponent::Float64,
    L::Float64,
    r::Float64,
    q_max_reverse::Float64,
    q_min_forward::Float64
)
```

Add constraints that model frictional head loss across a pipe. Here, `wm` is the WaterModels object; `n` is the subnetwork (or time) index that is considered; `a` is the index of the pipe; `node_fr` is the index of the tail node of the pipe; `node_to` is the index of the head node of the pipe; `exponent` is the exponent on flow in the head loss function (i.e., 1.852 for Hazen-Williams head loss and 2.0 for Darcy-Weisbach head loss); `L` is the length of the pipe; `r` is the resistance per unit length of the pipe; `q_max_reverse` is the *maximum* (negative) amount of flow when flow is traveling in the negative direction (which corresponds to the *minimum* magnitude of flow when traveling in the negative direction); and `q_min_forward` is the *minimum* (positive) amount of flow when flow is traveling in the positive (forward) direction.
