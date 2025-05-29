```julia
get_fuel_cost(
    component::PowerSystems.StaticInjection;
    start_time,
    len
) -> Union{Float64, TimeSeries.TimeArray}

```

コンポーネントの変動コストの燃料コストを取得します。これは `FuelCurve` でなければなりません。
