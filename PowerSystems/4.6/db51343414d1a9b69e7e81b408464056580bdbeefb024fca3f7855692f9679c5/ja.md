```julia
get_time_limits(
    value::PowerSystems.HydroDispatch
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`HydroDispatch`](@ref) の `time_limits` を取得します。
