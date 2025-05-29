```julia
Deterministic(
    name::AbstractString,
    input_data::AbstractDict{Dates.DateTime, <:TimeSeries.TimeArray};
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

DeterministicをTimeArraysのDictから構築します。

# 引数

  * `name::AbstractString`: ユーザー定義の名前
  * `input_data::AbstractDict{Dates.DateTime, TimeSeries.TimeArray}`: 時系列データ。
  * `normalization_factor::NormalizationFactor = 1.0`: 各データエントリに適用するオプションの正規化係数
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: データがスケーリング係数である場合、この関数はコンポーネントに対して呼び出され、[`get_time_series_array`](@ref)が呼ばれたときにデータに適用されます。
  * `timestamp = :timestamp`: 値がDataFramesとして渡される場合、これはタイムスタンプを含む列名でなければなりません。
