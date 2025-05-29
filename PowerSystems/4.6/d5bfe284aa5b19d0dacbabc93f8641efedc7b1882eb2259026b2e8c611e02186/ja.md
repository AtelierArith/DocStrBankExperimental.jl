```julia
get_time_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`ThermalMultiStart`](@ref) の `time_limits` を取得します。
