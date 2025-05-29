```julia
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime}
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime},
    len::Union{Nothing, Int64}
) -> Any
get_time_series(
    owner::Union{InfrastructureSystems.InfrastructureSystemsComponent, InfrastructureSystems.SupplementalAttribute},
    key::InfrastructureSystems.TimeSeriesKey,
    start_time::Union{Nothing, Dates.DateTime},
    len::Union{Nothing, Int64},
    count::Union{Nothing, Int64}
) -> Any

```

時間系列のキーを使用して、時間系列に保存されたデータを正確に返します。

デフォルトでは、すべての予測ウィンドウがメモリにロードされます。どれだけのデータが保存されているかに注意してください。

データのサブセットのみが必要な場合は、start_timeとlenを指定してください。

スケーリングファクタの乗数は適用されません。

# 引数

  * `owner::TimeSeriesOwners`: 時間系列を含むコンポーネントまたは属性
  * `key::TimeSeriesKey`: 時間系列のキー
  * `start_time::Union{Nothing, Dates.DateTime} = nothing`: 何も指定しない場合、時間系列の`initial_timestamp`を使用します。時間系列がForecastのサブタイプである場合、`start_time`はウィンドウの最初のタイムスタンプでなければなりません。
  * `len::Union{Nothing, Int} = nothing`: 時間次元の長さ。何も指定しない場合、全長を使用します。
  * `count::Union{Nothing, Int} = nothing`: Forecastのサブタイプにのみ適用されます。返す`start_time`からの予測ウィンドウの数。デフォルトでは、利用可能なすべてのウィンドウです。
  * `features...`: 同じコンポーネント属性の複数の時間系列配列を区別するユーザー定義のタグ。異なるシナリオや年のための異なる配列など。

参照: [`get_time_series` by name](@ref get_time_series(     ::Type{T},     owner::TimeSeriesOwners,     name::AbstractString;     start_time::Union{Nothing, Dates.DateTime} = nothing,     len::Union{Nothing, Int} = nothing,     count::Union{Nothing, Int} = nothing,     features..., ) where {T <: TimeSeriesData})
