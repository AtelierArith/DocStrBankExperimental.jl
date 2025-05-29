```julia
get_time_series(
    ::Type{T<:InfrastructureSystems.TimeSeriesData},
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    name::AbstractString;
    start_time,
    len,
    count,
    resolution,
    features...
) -> Any

```

時系列の正確に保存されたデータを返します

デフォルトでは、すべての予測ウィンドウがメモリにロードされます。どれだけのデータが保存されているかに注意してください。

データのサブセットのみが必要な場合は、`start_time`と`len`を指定してください。

スケーリングファクタの乗数は適用されません。

# 引数

  * `::Type{T}`: 返す`TimeSeriesData`の具体的なサブタイプ
  * `owner::TimeSeriesOwners`: 時系列を含むコンポーネントまたは属性
  * `name::AbstractString`: 時系列の名前
  * `resolution::Union{Nothing, Dates.Period} = nothing`: 時系列を一意に特定するために解像度が必要な場合は必須。
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 何も指定しない場合、時系列の`initial_timestamp`を使用します。TがForecastのサブタイプである場合、`start_time`はウィンドウの最初のタイムスタンプでなければなりません。
  * `len::Union{Nothing, Int} = nothing`: 時間次元の長さ。何も指定しない場合、全長を使用します。
  * `count::Union{Nothing, Int} = nothing`: Forecastのサブタイプにのみ適用されます。返す予測ウィンドウの数。デフォルトでは、利用可能なすべてのウィンドウです。
  * `features...`: 同じコンポーネント属性の異なるシナリオや年のための異なる配列など、複数の時系列配列を区別するユーザー定義のタグ

参照: [`get_time_series_array`](@ref), [`get_time_series_values`](@ref), [`get_time_series` by key](@ref get_time_series(     owner::TimeSeriesOwners,     key::TimeSeriesKey,     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     count::Union{Nothing, Int} = nothing, ))
