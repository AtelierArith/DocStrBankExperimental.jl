```julia
get_voltage_limits(
    value::PowerSystems.ACBus
) -> Union{Nothing, @NamedTuple{min::Float64, max::Float64}}

```

Get [`ACBus`](@ref) `voltage_limits`.
