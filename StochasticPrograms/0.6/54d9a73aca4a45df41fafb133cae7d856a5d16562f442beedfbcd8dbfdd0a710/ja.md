```
dual_objective_value(stochasticprogram::StochasticProgram, stage::Integer, scenario_index::Integer; result::Int = 1)
```

ステージ `stage` とシナリオ `scenario_index` に関連する双対問題の目的値を、最も最近の解に対する結果インデックス `result` の呼び出し後に `optimize!(stochasticprogram)` を実行した後に返します。
