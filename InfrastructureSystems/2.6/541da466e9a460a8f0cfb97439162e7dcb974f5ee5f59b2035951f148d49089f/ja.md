```julia
Probabilistic(
    name::AbstractString,
    input_data::AbstractDict{Dates.DateTime, <:TimeSeries.TimeArray},
    percentiles::Vector{Float64};
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Probabilistic

```

TimeArraysのDictからProbabilisticを構築します。

# 引数

  * `name::AbstractString`: ユーザー定義の名前
  * `input_data::AbstractDict{Dates.DateTime, TimeSeries.TimeArray}`: 時系列データ。
  * `percentiles`: 確率的予測で表されるパーセンタイル
  * `normalization_factor::NormalizationFactor = 1.0`: 各データエントリに適用するオプションの正規化係数
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: データがスケーリング係数である場合、この関数がコンポーネントに対して呼び出され、[`get_time_series_array`](@ref)が呼ばれたときにデータに適用されます。
  * `timestamp = :timestamp`: 値がDataFramesとして渡される場合、これはタイムスタンプを含む列名でなければなりません。
