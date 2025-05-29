```
get_timestep_switch_optimization_metadata(
    optimal_switching_results::Dict{String,Any};
    opt_switch_algorithm::String="full-lookahead"
)::Vector{Dict{String,Any}}
```

Gets the metadata from the optimal switching results for each timestep, returning a list of `Dicts` (if `opt_switch_algorithm="iterative`), or a list with a single `Dict` (if `opt_switch_algorithm="full-lookahead"`).
