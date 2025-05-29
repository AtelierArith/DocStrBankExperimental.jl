```julia
get_voltage_limits(
    value::PowerSystems.ACBus
) -> Union{Nothing, @NamedTuple{min::Float64, max::Float64}}

```

[`ACBus`](@ref) の `voltage_limits` を取得します。
