```
has_duals(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

ノードのステージ `stage` とシナリオ `scenario_index` において、結果インデックス `result` でクエリ可能な双対解がソルバーに存在する場合は `true` を返し、そうでない場合は `false` を返します。
