```julia
set_start_up!(
    value::PowerSystems.MarketBidCost,
    val::Real
) -> NamedTuple{(:hot, :warm, :cold), <:Tuple{Any, Float64, Float64}}

```

Auxiliary Method for setting up start up that are not multi-start
