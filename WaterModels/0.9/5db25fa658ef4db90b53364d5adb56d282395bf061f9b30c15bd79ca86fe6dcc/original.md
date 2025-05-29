```
constraint_source_directionality(
    wm::AbstractNCModel,
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

Currently does nothing for models of type `AbstractNCModel`. Here, `wm` is the WaterModels object; `n` is the subnetwork (time) index; `i` is the index of the node; and `pipe_fr`, `pipe_to`, etc., are indices of node-connecting components that are directed *from* or *to* node `i`, respectively.
