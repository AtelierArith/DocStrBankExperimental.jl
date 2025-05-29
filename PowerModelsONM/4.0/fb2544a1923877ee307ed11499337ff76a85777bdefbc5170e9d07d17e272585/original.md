```
get_timestep_generator_profiles!(
    args::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

Gets generator profile statistics for each timestep in-place in args, for use in [`entrypoint`](@ref entrypoint), using [`get_timestep_generator_profiles`](@ref get_timestep_generator_profiles)
