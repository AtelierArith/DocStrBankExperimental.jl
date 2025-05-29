```julia
get_time_series_array(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries;
    ...
) -> Any
get_time_series_array(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries,
    start_time::Union{Nothing, Dates.DateTime};
    len,
    ignore_scaling_factors
) -> Any

```

キャッシュされた `StaticTimeSeries` インスタンスから `TimeSeries.TimeArray` を返します。

時間系列データがスケーリングファクターである場合、返されるデータはデフォルトでスケーリングファクターマルチプライヤーによってスケーリングされます。

# 引数

  * `owner::TimeSeriesOwners`: 時間系列を含むコンポーネントまたは属性
  * `time_series::StaticTimeSeries`: `StaticTimeSeries` のサブタイプ（例：`SingleTimeSeries`）
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 取得する最初のタイムスタンプ。何も指定しない場合は、時間系列の `initial_timestamp` を使用します。
  * `len::Union{Nothing, Int} = nothing`: 取得する時間系列の長さ（すなわち、タイムスタンプの数）。何も指定しない場合は、全長を使用します。
  * `ignore_scaling_factors = false`: `true` の場合、時間系列データは `owner` の `scaling_factor_multiplier` 関数を呼び出した結果で乗算されます。

参照： [`get_time_series_values`](@ref get_time_series_values(owner::TimeSeriesOwners, time_series::StaticTimeSeries, start_time::Union{Nothing, Dates.DateTime} = nothing; len::Union{Nothing, Int} = nothing, ignore_scaling_factors = false)), [`get_time_series_timestamps`](@ref get_time_series_timestamps(owner::TimeSeriesOwners, time_series::StaticTimeSeries, start_time::Union{Nothing, Dates.DateTime} = nothing; len::Union{Nothing, Int} = nothing,)), [`StaticTimeSeriesCache`](@ref), [`get_time_series_array` by name from storage](@ref get_time_series_array(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_array` from a `ForecastCache`](@ref get_time_series_array(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len = nothing,     ignore_scaling_factors = false, ))
