```
fit(
  scenario_pairs::AbstractVector{Pair{Symbol, C}},
  parameters_fitted::DataFrame;
  kwargs...
) where C<:AbstractScenario
```

実験測定にパラメータをフィットします。`FitResult`型を返します。

引数:

  * `scenario_pairs` : 名前とタイプ[`Scenario`](@ref)のシナリオを含むペアのベクター
  * `parameters_fitted` : 最適化パラメータの設定とその初期値を持つDataFrame、[`read_parameters`](@ref)を参照
  * `kwargs...` : `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`でサポートされている他のODEソルバーおよび`fit`引数
