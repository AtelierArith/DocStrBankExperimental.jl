```
get_timestep_dispatch_optimization_metadata!(
    args::Dict{String,<:Any}
)::Dict{String,Any}
```

Retrieves the switching optimization results metadata from the optimal switching solution via [`get_timestep_dispatch_optimization_metadata`](@ref get_timestep_dispatch_optimization_metadata) and applies it in-place to args, for use with [`entrypoint`](@ref entrypoint)
