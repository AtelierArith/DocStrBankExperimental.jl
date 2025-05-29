```
get_timestep_stability!(
    args::Dict{String,<:Any}
)::Vector{Bool}
```

Gets the stability at each timestep and applies it in-place to args, for use in [`entrypoint`](@ref entrypoint), using [`get_timestep_stability`](@ref get_timestep_stability)
