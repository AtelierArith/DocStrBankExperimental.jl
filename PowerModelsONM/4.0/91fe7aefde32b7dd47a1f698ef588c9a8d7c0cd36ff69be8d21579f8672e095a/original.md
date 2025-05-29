```
get_timestep_storage_soc(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any}
)::Vector{Real}
```

Returns the storage state of charge, i.e., how much energy is remaining in all of the the energy storage DER based on the optimal dispatch `solution`. Needs `network` to give percentage.
