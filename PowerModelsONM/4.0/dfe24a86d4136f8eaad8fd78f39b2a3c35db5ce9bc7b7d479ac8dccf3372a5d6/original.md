```
get_timestep_bus_types!(args::Dict{String,<:Any})::Vector{Dict{String,String}}
```

Gets bus types (PQ, PV, ref, isolated) for each timestep from the optimal dispatch result and assigns it to `args["output_data"]["Protection settings"]["bus_types"]`
