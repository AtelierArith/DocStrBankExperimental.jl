```julia
get_storage_level_limits(
    value::PowerSystems.EnergyReservoirStorage
) -> @NamedTuple{min::Float64, max::Float64}

```

[`EnergyReservoirStorage`](@ref) の `storage_level_limits` を取得します。
