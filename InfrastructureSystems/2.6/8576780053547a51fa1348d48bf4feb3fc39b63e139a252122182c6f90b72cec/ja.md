```julia
Scenarios(
    name::AbstractString,
    input_data::AbstractDict,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Scenarios

```

SortedDictの配列からScenariosを構築します。

# 引数

  * `name::AbstractString`: ユーザー定義の名前
  * `input_data::AbstractDict{Dates.DateTime, Matrix{Float64}}`: 時系列データ。
  * `resolution::Dates.Period`: Dates.Periodでの予測の解像度
  * `normalization_factor::NormalizationFactor = 1.0`: 各データエントリに適用するオプションの正規化係数
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: データがスケーリング係数である場合、この関数はコンポーネントに対して呼び出され、[`get_time_series_array`](@ref)が呼び出されるときにデータに適用されます。
