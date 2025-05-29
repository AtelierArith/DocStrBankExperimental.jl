```
get_timestep_dispatch_optimization_metadata(
    optimal_dispatch_result::Dict{String,Any}
)::Dict{String,Any}
```

Gets the metadata from the optimal switching results for each timestep, returning a list of Dicts (if `opt_switch_algorithm="rolling-horizon"`), or a list with a single Dict (if `opt_switch_algorithm="full-lookahead"`).
