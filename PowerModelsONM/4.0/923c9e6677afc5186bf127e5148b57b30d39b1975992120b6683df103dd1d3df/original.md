```
get_timestep_voltage_statistics(
    solution::Dict{String,<:Any},
    network::Dict{String,<:Any};
    make_per_unit::Bool=true
)::Dict{String,Vector{Real}}
```

Returns statistics on the Minimum, Mean, and Maximum voltages for each timestep using [`get_voltage_min_mean_max`](@ref get_voltage_min_mean_max)

If `make_per_unit` (default: true), will return voltage statistics in per-unit representation. If `make_per_unit` is false, and there are different voltage bases across the network, the statistics will not make sense.
