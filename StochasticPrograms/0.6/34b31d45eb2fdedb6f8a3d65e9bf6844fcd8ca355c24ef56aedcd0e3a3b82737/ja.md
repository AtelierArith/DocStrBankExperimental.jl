```
objective_value(stochasticprogram::StochasticProgram; result::Int = 1)
```

最も最近の解に対する結果インデックス `result` に関連付けられた目的値を返します。これは `optimize!(stochasticprogram)` を呼び出した後のものです。
