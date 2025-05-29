```
get_timestep_switch_changes(
    network::Dict{String,<:Any},
    optimal_switching_results::Dict{String,<:Any}=Dict{String,Any}()
)::Vector{Vector{String}}
```

Gets a list of switches whose state has changed between timesteps (always expect the first timestep to be an empty list). This expects the solutions from the MLD problem to have been merged into `network`
