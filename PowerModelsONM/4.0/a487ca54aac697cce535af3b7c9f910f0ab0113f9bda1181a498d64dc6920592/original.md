```
get_timestep_device_actions(
    network::Dict{String,<:Any},
    optimal_switching_results::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

From the multinetwork `network`, determines the switch configuration at each timestep. If the switch does not exist in `mld_results`, the state will default back to the state given in the original network. This could happen if the switch is not dispatchable, and therefore `state` would not be expected in the results.

Will output Vector{Dict} where each Dict will contain `"Switch configurations"`, which is a Dict with switch names as keys, and the switch state, `"open"` or `"closed"` as values, and `"Shedded loads"`, which is a list of load names that have been shed at that timestep.
