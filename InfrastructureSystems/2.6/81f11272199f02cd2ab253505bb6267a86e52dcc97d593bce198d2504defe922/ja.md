```julia
get_time_series_timestamps(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    resolution,
    start_time,
    len,
    features...
) -> Vector{D} where D<:Dates.TimeType

```

指定された時系列パラメータに基づいてストレージからタイムスタンプのベクターを返します。

# 引数

  * `::Type{T}`: 時系列の型（`TimeSeriesData`の具体的なサブタイプ）
  * `owner::TimeSeriesOwners`: 時系列を含むコンポーネントまたは属性
  * `name::AbstractString`: 時系列の名前
  * `resolution::Union{Nothing, Dates.Period} = nothing`: 時系列を一意に識別するために必要な場合。
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 何も指定しない場合、時系列の`initial_timestamp`を使用します。Tが[`Forecast`](@ref)のサブタイプである場合、`start_time`はウィンドウの最初のタイムスタンプでなければなりません。
  * `len::Union{Nothing, Int} = nothing`: 取得する時系列の長さ（すなわち、タイムスタンプの数）。何も指定しない場合、全長を使用します。
  * `features...`: 同じコンポーネント属性の異なるシナリオや年のための異なる配列など、複数の時系列配列を区別するユーザー定義のタグ

参照: [`get_time_series_array`](@ref get_time_series_array(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_values`](@ref get_time_series_values(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, features...,) where {T <: TimeSeriesData}), [`get_time_series_timestamps` from a `StaticTimeSeriesCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, )), [`get_time_series_timestamps` from a `ForecastCache`](@ref get_time_series_timestamps(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing, ))
