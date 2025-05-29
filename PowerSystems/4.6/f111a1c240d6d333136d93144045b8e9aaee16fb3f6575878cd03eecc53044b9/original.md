```julia
get_start_time_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}

```

Get [`ThermalMultiStart`](@ref) `start_time_limits`.
