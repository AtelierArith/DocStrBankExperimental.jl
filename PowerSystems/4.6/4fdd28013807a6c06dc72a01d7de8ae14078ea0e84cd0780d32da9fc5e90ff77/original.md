```julia
get_start_up(
    value::PowerSystems.MarketBidCost
) -> Union{@NamedTuple{hot::Float64, warm::Float64, cold::Float64}, InfrastructureSystems.TimeSeriesKey}

```

Get [`MarketBidCost`](@ref) `start_up`.
