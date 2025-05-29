```julia
get_start_up(
    value::PowerSystems.StorageCost
) -> Union{Float64, @NamedTuple{charge::Float64, discharge::Float64}}

```

[`StorageCost`](@ref) `start_up`を取得します。
