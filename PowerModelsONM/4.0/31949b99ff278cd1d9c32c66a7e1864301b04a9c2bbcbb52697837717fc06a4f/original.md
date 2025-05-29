```
get_timestep_dispatch(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

Returns the dispatch information for generation assets (generator, storage, solar, voltage_source) and bus voltage magnitudes in SI units for each timestep from the optimal dispatch `solution`
