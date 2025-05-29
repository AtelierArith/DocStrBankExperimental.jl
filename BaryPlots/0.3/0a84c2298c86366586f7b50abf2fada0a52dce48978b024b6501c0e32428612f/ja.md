```
struct ReplicatorParams
```

レプリケーター動力学のためのパラメータを保持し、ペイオフ関数や追加のパラメータを含みます。

# フィールド

  * `payoff_functions`: 各戦略に対して1つずつの3つのペイオフ関数 `(payoff1, payoff2, payoff3)` のタプル。
  * `extra_params`: ペイオフ関数に必要な追加のパラメータを含む `NamedTuple`。
