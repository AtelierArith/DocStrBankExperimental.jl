```
get_timestep_storage_soc!(
    args::Dict{String,<:Any}
)::Vector{Real}
```

Gets storage energy remaining percentage for each timestep in-place in args, for use in [`entrypoint`](@ref entrypoint), using [`get_timestep_storage_soc`](@ref get_timestep_storage_soc)
