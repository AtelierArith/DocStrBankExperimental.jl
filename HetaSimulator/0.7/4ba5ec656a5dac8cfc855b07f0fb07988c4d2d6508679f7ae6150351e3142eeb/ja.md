```
function estimator(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::DataFrame;
  kwargs...
) where C<:AbstractScenario
```

パラメータの特定と分析のための尤度推定器関数を生成します。これは `DataFrame` からのパラメータのインターフェースです。詳細は基本の `estimator` メソッドを参照してください。

引数:

  * `scenario_pairs` : 名前とタイプ [`Scenario`](@ref) のシナリオを含むペアのベクター
  * `parameters_fitted` : 最適化パラメータの設定とその初期値を持つ DataFrame、[`read_parameters`](@ref) を参照
  * `kwargs...` : `estimator` によってサポートされる他の引数、基本メソッドを参照。
