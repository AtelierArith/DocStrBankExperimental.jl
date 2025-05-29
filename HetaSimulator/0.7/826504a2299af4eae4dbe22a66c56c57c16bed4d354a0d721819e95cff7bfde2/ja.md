```
mc(scenario::Scenario,
  parameters_variation::DataFrame,
  num_iter::Int;
  kwargs...
)
```

単一のシナリオ `Scenario` でモンテカルロシミュレーションを実行します。[`MCResult`](@ref) 型を返します。

例: `mc(scn1, DataFrame(k2=rand(3),k3=rand(3)), 1000)`

引数:

  * `scenario` : [`Scenario`](@ref) 型のシミュレーションシナリオ
  * `parameters_variation` : 事前に生成されたパラメータを持つ DataFrame。
  * `num_iter` : モンテカルロイテレーションの数
  * kwargs : `mc(scenario::Scenario, parameters_variation::Vector, num_iter::Int64)` でサポートされている他のソルバー関連の引数
