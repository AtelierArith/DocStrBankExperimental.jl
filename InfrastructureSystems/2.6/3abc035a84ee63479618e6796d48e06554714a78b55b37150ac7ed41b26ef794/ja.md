```julia
Probabilistic(
    name::AbstractString,
    input_data::AbstractDict,
    percentiles::Vector,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Probabilistic

```

SortedDictの配列からProbabilisticを構築します。

# 引数

  * `name::AbstractString`: ユーザー定義の名前
  * `input_data::AbstractDict{Dates.DateTime, Matrix{Float64}}`: 時系列データ。
  * `percentiles`: 確率的予測で表されるパーセンタイル
  * `resolution::Dates.Period`: Dates.Periodでの予測の解像度
  * `normalization_factor::NormalizationFactor = 1.0`: 各データエントリに適用するオプションの正規化因子
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: データがスケーリング因子である場合、この関数がコンポーネントに対して呼び出され、[`get_time_series_array`](@ref)が呼び出されたときにデータに適用されます。
