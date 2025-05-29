```julia
add_time_series!(
    sys::PowerSystems.System,
    component::PowerSystems.Component,
    time_series::InfrastructureSystems.TimeSeriesData;
    features...
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

コンポーネントに時系列データを追加します。

コンポーネントがシステムに保存されていない場合、ArgumentErrorをスローします。
