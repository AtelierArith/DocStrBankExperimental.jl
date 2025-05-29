```
get_timestep_inverter_states(optimal_switching_results::Dict{String,<:Any})::Vector{Dict{String,Any}}
```

Gets 'inverter' state for each generation object at each timestep from `optimal_switching_results`. Defaults to `GRID_FORMING` if no inverter state is available.
