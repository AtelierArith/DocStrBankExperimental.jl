```julia
set_service_bid!(
    sys::PowerSystems.System,
    component::PowerSystems.StaticInjection,
    service::PowerSystems.Service,
    time_series_data::InfrastructureSystems.TimeSeriesData,
    power_units::InfrastructureSystems.UnitSystemModule.UnitSystem
)

```

マーケットビッドコストにサービスビッドの時系列データを追加します。

# 引数

  * `sys::System`: PowerSystem システム
  * `component::StaticInjection`: 静的インジェクションデバイス
  * `service::Service,`: デバイスが貢献する資格のあるサービス
  * `time_series_data::IS.TimeSeriesData`: 時系列データ
