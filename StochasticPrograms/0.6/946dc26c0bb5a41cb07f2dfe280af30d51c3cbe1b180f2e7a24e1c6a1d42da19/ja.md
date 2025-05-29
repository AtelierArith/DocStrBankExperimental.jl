```
has_duals(stochasticprogram::TwoStageStochasticProgram, scenario_index::Integer; result::Int = 1)
```

シナリオ `scenario_index` の結果インデックス `result` で、ソルバーが双対解をクエリできる場合は `true` を返し、そうでない場合は `false` を返します。
