```
check_switch_state_feasibility(data::Dict{String,<:Any})::Union{Dict{String,Bool},Bool}
```

Helper function to aid users in determining whether network model has a feasible starting switch configuration (at each time step, if the network model is multinetwork), assuming radiality constraints are applied.
