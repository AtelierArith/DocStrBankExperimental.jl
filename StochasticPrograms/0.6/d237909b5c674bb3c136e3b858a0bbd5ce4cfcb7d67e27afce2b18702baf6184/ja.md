```
dual_objective_value(stochasticprogram::StochasticProgram; result::Int = 1)
```

最も最近の解に対する `optimize!(stochasticprogram)` の呼び出し後の結果インデックス `result` に関連付けられた双対問題の目的値を返します。
