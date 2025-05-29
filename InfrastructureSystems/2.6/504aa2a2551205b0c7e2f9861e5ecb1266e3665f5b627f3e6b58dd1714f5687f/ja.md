```julia
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    forecast::InfrastructureSystems.Forecast;
    ...
)
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    forecast::InfrastructureSystems.Forecast,
    start_time::Union{Nothing, Dates.DateTime};
    len
) -> Vector{D} where D<:Dates.TimeType

```

キャッシュされたForecastインスタンスからタイムスタンプのベクターを返します。

# 引数

  * `owner::TimeSeriesOwners`: タイムシリーズを含むコンポーネントまたは属性
  * `forecast::Forecast`: [`Forecast`](@ref) の具体的なサブタイプ
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 予測ウィンドウのいずれかの最初のタイムスタンプ
  * `len::Union{Nothing, Int} = nothing`: 取得するタイムシリーズの長さ（すなわち、タイムスタンプの数）。何も指定しない場合は、全長を使用します。

参照: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values`](@ref get_time_series_values(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`ForecastCache`](@ref), [`get_time_series_timestamps` by name from storage](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `StaticTimeSeriesCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
