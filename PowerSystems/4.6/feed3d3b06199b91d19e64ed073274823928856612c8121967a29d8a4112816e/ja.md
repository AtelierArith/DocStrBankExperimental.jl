```julia
get_variable_cost(
    service::PowerSystems.ReserveDemandCurve;
    start_time,
    len
) -> Union{InfrastructureSystems.CostCurve{InfrastructureSystems.PiecewiseIncrementalCurve}, TimeSeries.TimeArray}

```

`ReserveDemandCurve`の変動コストデータを取得します。ユーザーは`start_time`と`len`を指定でき、関数は`CostCurve`の`TimeArray`を返します。
