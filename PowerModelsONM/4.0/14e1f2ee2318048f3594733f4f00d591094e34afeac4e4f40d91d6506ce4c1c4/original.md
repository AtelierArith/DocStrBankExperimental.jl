```
get_timestep_fault_study_metadata(
    fault_studies_results::Dict{String,Any}
)::Vector{Dict{String,Any}}
```

Gets the metadata from the optimal switching results for each timestep, returning a list of Dicts (if `opt_switch_algorithm="rolling-horizon"`), or a list with a single Dict (if `opt_switch_algorithm="full-lookahead"`).
