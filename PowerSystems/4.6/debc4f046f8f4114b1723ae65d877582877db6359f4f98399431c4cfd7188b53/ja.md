```julia
get_voltage_limits(
    value::PowerSystems.DCBus
) -> Union{Nothing, @NamedTuple{min::Float64, max::Float64}}

```

[`DCBus`](@ref) の `voltage_limits` を取得します。
