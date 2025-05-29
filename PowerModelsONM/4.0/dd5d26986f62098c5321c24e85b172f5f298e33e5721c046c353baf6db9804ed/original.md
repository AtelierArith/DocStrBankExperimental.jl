```
get_timestep_voltage_statistics!(
    args::Dict{String,<:Any}
)::Dict{String,Vector{Real}}
```

Gets voltage statistics min, mean, max for each timestep in-place in args, for use in [`entrypoint`][@ref entrypoint], using [`get_timestep_voltage_statistics`](@ref get_timestep_voltage_statistics)
