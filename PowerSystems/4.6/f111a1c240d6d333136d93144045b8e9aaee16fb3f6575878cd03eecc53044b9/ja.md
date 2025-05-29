```julia
get_start_time_limits(
    value::PowerSystems.ThermalMultiStart
) -> Union{Nothing, @NamedTuple{hot::Float64, warm::Float64, cold::Float64}}

```

[`ThermalMultiStart`](@ref) の `start_time_limits` を取得します。
