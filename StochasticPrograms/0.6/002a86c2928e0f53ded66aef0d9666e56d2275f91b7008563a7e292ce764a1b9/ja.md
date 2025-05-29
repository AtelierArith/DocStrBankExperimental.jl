```
dual_objective_value(stochasticprogram::TwoStageStochasticProgram, scenario_index::Integer; result::Int = 1)
```

シナリオ `scenario_index` に関連する双対問題の目的値を、`optimize!(stochasticprogram)` の呼び出し後の最新の解の結果インデックス `result` に基づいて返します。
