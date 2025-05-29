```
get_timestep_inverter_states!(args::Dict{String,<:Any})::Vector{Dict{String,Any}}
```

Adds field "inverter" to power flow output for inverter objects, i.e., storage generator, voltage*source, solar. See [`get*timestep*inverter*states`](@ref get*timestep*inverter_states)
