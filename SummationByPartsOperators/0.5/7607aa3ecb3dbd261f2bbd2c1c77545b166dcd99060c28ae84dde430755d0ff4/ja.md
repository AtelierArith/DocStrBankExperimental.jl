```
semidiscretize(u0func, semi::AbstractSemidiscretization, tspan)
```

初期データ `u0func` に対して半離散化 `semi` を適用し、時間範囲 `tspan` を持つ `ODEProblem` を返します。
