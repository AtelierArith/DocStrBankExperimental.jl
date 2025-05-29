```
optimal_decision(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer)
```

`stochasticprogram`の`stage`ステージおよび`scenario_index`シナリオのノードにおける最適な決定を返します。これは`optimize!(stochasticprogram)`を呼び出した後の結果です。
