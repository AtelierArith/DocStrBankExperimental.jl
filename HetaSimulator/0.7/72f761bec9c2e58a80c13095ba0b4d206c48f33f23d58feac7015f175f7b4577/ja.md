```
fit(
  scenarios::AbstractVector{C},
  parameters_fitted;
  kwargs...
) where C<:AbstractScenario
```

実験測定にパラメータをフィットします。`FitResult`型を返します。

例:

`fit([scn2, scn3, scn4], [:k1=>0.1,:k2=>0.2,:k3=>0.3])`

引数:

  * `scenarios` : [`Scenario`](@ref)型のシナリオのベクトル
  * `parameters_fitted` : 最適化パラメータとその初期値
  * `kwargs...` : `fit(scenario_pairs::Vector{<:Pair}, parameters_fitted::Vector{<:Pair}`でサポートされている他のODEソルバーおよび`fit`関連の引数
