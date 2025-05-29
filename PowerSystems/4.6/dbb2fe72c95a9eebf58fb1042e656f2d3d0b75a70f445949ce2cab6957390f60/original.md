```julia
get_fuel_cost(
    component::PowerSystems.StaticInjection;
    start_time,
    len
) -> Union{Float64, TimeSeries.TimeArray}

```

Get the fuel cost of the component's variable cost, which must be a `FuelCurve`.
