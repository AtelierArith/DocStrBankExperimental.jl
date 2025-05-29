```julia
get_time_series_values(
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

ストレージからタイムスタンプなしの時系列データのベクトルを返します

データサイズが小さく、これが何度も呼び出される場合は、キャッシュされた `TimeSeriesData` インスタンスを受け入れるバージョンを使用することを検討してください。

# 引数

  * `::Type{T}`: 時系列の型（`TimeSeriesData` の具体的なサブタイプ）
  * `owner::TimeSeriesOwners`: 時系列を含むコンポーネントまたは属性
  * `name::AbstractString`: 時系列の名前
  * `resolution::Union{Nothing, Dates.Period} = nothing`: 時系列を一意に識別するために必要な場合
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 何も指定しない場合、時系列の `initial_timestamp` を使用します。T が [`Forecast`](@ref) のサブタイプである場合、`start_time` はウィンドウの最初のタイムスタンプでなければなりません。
  * `len::Union{Nothing, Int} = nothing`: 取得する時系列の長さ（すなわち、タイムスタンプの数）。何も指定しない場合、全長を使用します。
  * `ignore_scaling_factors = false`: `true` の場合、時系列データは `owner` の `scaling_factor_multiplier` 関数を呼び出した結果で乗算されます
  * `features...`: 同じコンポーネント属性の異なるシナリオや年のための異なる配列など、複数の時系列配列を区別するユーザー定義のタグ

参照: [`get_time_series_array`](@ref get_time_series_array(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false,     features..., ) where {T <: TimeSeriesData}), [`get_time_series_timestamps`](@ref get_time_series_timestamps(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData}), [`get_time_series`](@ref), [`get_time_series_values` from a `StaticTimeSeriesCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     time_series::StaticTimeSeries,     start_time::Union{Nothing, Dates.DateTime} = nothing;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, )), [`get_time_series_values` from a `ForecastCache`](@ref get_time_series_values(     owner::TimeSeriesOwners,     forecast::Forecast,     start_time::Dates.DateTime;     len::Union{Nothing, Int} = nothing,     ignore_scaling_factors = false, ))
