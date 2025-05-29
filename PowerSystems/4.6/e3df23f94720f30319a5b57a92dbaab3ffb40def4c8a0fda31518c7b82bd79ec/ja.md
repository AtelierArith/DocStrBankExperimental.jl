```julia
get_time_limits(
    value::PowerSystems.HydroEnergyReservoir
) -> Union{Nothing, @NamedTuple{up::Float64, down::Float64}}

```

[`HydroEnergyReservoir`](@ref) の `time_limits` を取得します。
