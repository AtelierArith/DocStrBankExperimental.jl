```
objective_value(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

最も最近の解に対する `optimize!(stochasticprogram)` の呼び出し後に、結果インデックス `result` に関連付けられたステージ `stage` とシナリオ `scenario_index` のノードの目的値を返します。
