```julia
set_variable_cost!(
    sys::PowerSystems.System,
    component::PowerSystems.ReserveDemandCurve,
    data::Union{Nothing, InfrastructureSystems.TimeSeriesData}
) -> Union{InfrastructureSystems.ForecastKey, InfrastructureSystems.StaticTimeSeriesKey}

```

ReserveDemandCurveにエネルギー市場の入札時系列を追加します。

# 引数

  * `sys::System`: PowerSystem システム
  * `component::ReserveDemandCurve`: カーブ
  * `time_series_data::IS.TimeSeriesData`: 時系列データ
