```
get_timestep_device_actions!(args::Dict{String,<:Any})::Vector{Dict{String,Any}}
```

Gets the device actions at every timestep using [`get_timestep_device_actions`](@ref get_timestep_device_actions) and applies it in place to args, for use in [`entrypoint`](@ref entrypoint).
