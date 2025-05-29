```julia
get_time_limits(
    value::PowerSystems.ThermalStandard
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`ThermalStandard`](@ref) の `time_limits` を取得します。
