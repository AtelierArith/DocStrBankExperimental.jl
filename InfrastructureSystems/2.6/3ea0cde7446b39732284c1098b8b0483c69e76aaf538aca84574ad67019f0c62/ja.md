```julia
Deterministic(
    name::AbstractString,
    filename::AbstractString,
    component::InfrastructureSystems.InfrastructureSystemsComponent,
    resolution::Dates.Period;
    normalization_factor,
    scaling_factor_multiplier
) -> InfrastructureSystems.Deterministic

```

CSVファイルからDeterministicを構築します。最初の列はDateTime形式のタイムスタンプであり、列は予測ウィンドウ内の値です。

# 引数

  * `name::AbstractString`: ユーザー定義の名前
  * `filename::AbstractString`: データを含むCSVファイルの名前
  * `component::InfrastructureSystemsComponent`: データに関連付けられたコンポーネント
  * `normalization_factor::NormalizationFactor = 1.0`: 各データエントリに適用するオプションの正規化係数
  * `scaling_factor_multiplier::Union{Nothing, Function} = nothing`: データがスケーリング係数である場合、この関数はコンポーネントに対して呼び出され、[`get_time_series_array`](@ref)が呼び出されるときにデータに適用されます。
