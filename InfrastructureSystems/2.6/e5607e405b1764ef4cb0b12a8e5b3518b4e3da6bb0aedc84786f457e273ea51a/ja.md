```julia
get_time_series_values(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    forecast::InfrastructureSystems.Forecast,
    start_time::Dates.DateTime;
    len,
    ignore_scaling_factors
) -> Any

```

キャッシュされた `Forecast` インスタンスから、タイムスタンプなしの時系列データのベクトルを返します。

# 引数

  * `owner::TimeSeriesOwners`: 時系列を含むコンポーネントまたは属性
  * `forecast::Forecast`: [`Forecast`](@ref) の具体的なサブタイプ
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 予測ウィンドウの最初のタイムスタンプ
  * `len::Union{Nothing, Int} = nothing`: 取得する時系列の長さ（すなわち、タイムスタンプの数）。何も指定しない場合は、全長を使用します。
  * `ignore_scaling_factors = false`: `true` の場合、時系列データは `owner` の `scaling_factor_multiplier` 関数を呼び出した結果で乗算されます。

関連情報: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len = nothing,     ignore_scaling_factors = false, )), [`get_time_series_timestamps`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, )), [`ForecastCache`](@ref), [`get_time_series_values` by name from storage](@ref get_time_series_values(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_values` from a `StaticTimeSeriesCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, ))
