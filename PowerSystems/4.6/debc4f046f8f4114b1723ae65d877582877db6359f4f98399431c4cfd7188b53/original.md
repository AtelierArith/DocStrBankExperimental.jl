```julia
get_voltage_limits(
    value::PowerSystems.DCBus
) -> Union{Nothing, @NamedTuple{min::Float64, max::Float64}}

```

Get [`DCBus`](@ref) `voltage_limits`.
