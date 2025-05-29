```julia
get_variable_cost(
    service::PowerSystems.ReserveDemandCurve;
    start_time,
    len
) -> Union{InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, TimeSeries.TimeArray}

```

Retrieve the variable cost data for a `ReserveDemandCurve`. The user may specify `start_time` and `len` and the function returns a `TimeArray` of `CostCurve`s.
