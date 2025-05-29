```
get_timestep_bus_types(
    optimal_dispatch_solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Dict{String,String}}
```

Gets bus types (PQ, PV, ref, isolated) for each timestep from the `optimal_dispatch_solution`
