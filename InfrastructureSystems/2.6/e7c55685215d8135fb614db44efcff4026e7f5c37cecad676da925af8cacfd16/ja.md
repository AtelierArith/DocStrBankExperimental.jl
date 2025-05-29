```julia
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries;
    ...
) -> Vector{D} where D<:Dates.TimeType
get_time_series_timestamps(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    time_series::InfrastructureSystems.StaticTimeSeries,
    start_time::Union{Nothing, Dates.DateTime};
    len
) -> Vector{D} where D<:Dates.TimeType

```

キャッシュされた StaticTimeSeries インスタンスからタイムスタンプのベクトルを返します。

# 引数

  * `owner::TimeSeriesOwners`: タイムシリーズを含むコンポーネントまたは属性
  * `time_series::StaticTimeSeries`: `StaticTimeSeries` のサブタイプ（例: `SingleTimeSeries`）
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 取得する最初のタイムスタンプ。何も指定しない場合は、タイムシリーズの `initial_timestamp` を使用します。
  * `len::Union{Nothing, Int} = nothing`: 取得するタイムシリーズの長さ（すなわち、タイムスタンプの数）。何も指定しない場合は、全長を使用します。

参照: [`get_time_series_array`](@ref get_time_series_array(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values`](@ref get_time_series_values(owner::TimeSeriesOwners, time_series::StaticTimeSeries, start_time::Union{Nothing, Dates.DateTime} = nothing; len::Union{Nothing, Int} = nothing, ignore_scaling_factors = false)), [`StaticTimeSeriesCache`](@ref), [`get_time_series_timestamps` by name from storage](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `ForecastCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
