```
mc(scenario_pairs::Vector{<:AbstractScenario},
  parameters_variation::Vector{<:Pair},
  num_iter::Int64;
  kwargs...
)
```

単一シナリオでモンテカルロシミュレーションを実行します。`Vector{MCResult}`型を返します。

例: `mc([scn1,scn2], [:k2=>Normal(1e-3,1e-4), :k3=>Uniform(1e-4,1e-2)], 1000)`

引数:

  * `scenario_pairs` : [`Scenario`](@ref)型のシナリオのベクター
  * `parameters_variation` : パラメータの変動設定
  * `num_iter` : モンテカルロの反復回数
  * kwargs : `mc(scenario_pairs::Vector{<:Pair}, parameters_variation::Vector, num_iter::Int64)`でサポートされている他のソルバー関連の引数
