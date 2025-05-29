```
get_timestep_fault_study_metadata!(
    args::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

Retrieves the switching optimization results metadata from the optimal switching solution via [`get_timestep_fault_study_metadata`](@ref get_timestep_fault_study_metadata) and applies it in-place to args, for use with [`entrypoint`](@ref entrypoint)
