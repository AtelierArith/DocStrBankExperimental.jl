```
get_timestep_fault_currents!(
    args::Dict{String,<:Any}
)::Vector{Dict{String,Any}}
```

Gets fault currents for switches and corresponding fault from study in-place in args, for use in [`entrypoint`](@ref entrypoint), using [`get_timestep_fault_currents`](@ref get_timestep_fault_currents).
