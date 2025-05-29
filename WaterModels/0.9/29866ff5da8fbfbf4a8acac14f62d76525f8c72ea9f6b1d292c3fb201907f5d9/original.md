```
constraint_intermediate_directionality(
    wm::AbstractNCDModel,
    n::Int,
    i::Int,
    pipe_fr::Array{Int,1},
    pipe_to::Array{Int,1},
    des_pipe_fr::Array{Int,1},
    des_pipe_to::Array{Int,1},
    pump_fr::Array{Int,1},
    pump_to::Array{Int,1},
    regulator_fr::Array{Int,1},
    regulator_to::Array{Int,1},
    short_pipe_fr::Array{Int,1},
    short_pipe_to::Array{Int,1},
    valve_fr::Array{Int,1},
    valve_to::Array{Int,1}
)
```

Adds a constraint that ensures the direction of incoming flow at the node will be equal to the direction of outgoing flow. Note that this constraint should only be applied in situations where the degree of the node is two and there is zero supply or demand (i.e., the node is a "junction" or pass-through node). Here, `n` is the subnetwork (time) index; `i` is the index of the node; and `pipe_fr`, `pipe_to`, etc., are indices of node-connecting components that are directed *from* or *to* node `i`, respectively.
