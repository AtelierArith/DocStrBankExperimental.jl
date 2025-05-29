```julia
check_time_series_consistency(
    sys::PowerSystems.System,
    _::Type{T<:InfrastructureSystems.TimeSeriesData}
) -> Union{Nothing, Tuple{Any, Any}}

```

システム内の時系列の整合性をチェックします。

SingleTimeSeriesの場合、初期タイムスタンプと長さのタプルを返します。

これは、Forecastのサブタイプに対しては何もしません。なぜなら、それらはすでに整合性が保証されているからです。

いずれかの時系列が不整合である場合、InfrastructureSystems.InvalidValueをスローします。
