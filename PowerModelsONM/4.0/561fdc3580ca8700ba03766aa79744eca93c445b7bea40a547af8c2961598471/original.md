```
apply_switch_solutions!(network::Dict{String,<:Any}, optimal_switching_results::Dict{String,<:Any})::Dict{String,Any}
```

Updates a multinetwork `network` in-place with the results from optimal switching `optimal_switching_results`.

Used when not using the in-place version of [`optimize_switches!`](@ref optimize_switches!).
