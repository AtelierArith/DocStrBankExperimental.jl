```julia
add_time_series!(
    sys::PowerSystems.System,
    components,
    time_series::InfrastructureSystems.TimeSeriesData;
    features...
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

複数のコンポーネントに同じ時系列データを追加します。

この関数はデータの単一コピーを保存します。各コンポーネントはそのデータへの参照を保存します。これは、同じデータで各コンポーネントに対して `add_time_series!` を個別に呼び出すよりもはるかに効率的です。この場合、時系列配列は1つだけ保存されます。

コンポーネントがシステムに保存されていない場合、ArgumentErrorをスローします。
