```julia
get_time_series_array(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    resolution,
    start_time,
    len,
    ignore_scaling_factors,
    features...
) -> Any

```

指定された時系列パラメータに基づいてストレージから `TimeSeries.TimeArray` を返します。

時系列データがスケーリングファクターである場合、返されるデータはデフォルトでスケーリングファクターマルチプライヤーによってスケーリングされます。

デフォルトでは、すべての予測ウィンドウがメモリにロードされます。どれだけのデータが保存されているかに注意してください。

データのサブセットのみが必要な場合は、`start_time` と `len` を指定してください。

# 引数

  * `::Type{T}`: 時系列の型（`TimeSeriesData` の具体的なサブタイプ）
  * `owner::TimeSeriesOwners`: 時系列を含むコンポーネントまたは属性
  * `name::AbstractString`: 時系列の名前
  * `resolution::Union{Nothing, Dates.Period} = nothing`: 時系列を一意に識別するために必要な場合
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 何も指定しない場合、時系列の `initial_timestamp` を使用します。T が [`Forecast`](@ref) のサブタイプである場合、`start_time` はウィンドウの最初のタイムスタンプでなければなりません。
  * `len::Union{Nothing, Int} = nothing`: 取得する時系列の長さ（すなわち、タイムスタンプの数）。何も指定しない場合、全長を使用します。
  * `ignore_scaling_factors = false`: `true` の場合、時系列データは `owner` の保存された `scaling_factor_multiplier` 関数を呼び出した結果で乗算されます
  * `features...`: 同じコンポーネント属性の複数の時系列配列を区別するためのユーザー定義タグ（異なるシナリオや年のための異なる配列など）

参照: [`get_time_series_values`](@ref get_time_series_values(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, features...,) where {T <: TimeSeriesData}), [`get_time_series_timestamps`](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_array` from a `StaticTimeSeriesCache`](@ref get_time_series_array(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_array` from a `ForecastCache`](@ref get_time_series_array(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len = nothing,     ignore_scaling_factors = false, ))
