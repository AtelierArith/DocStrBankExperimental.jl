```
ContinuousTerm <: AbstractTerm
```

連続変数を表し、名前と要約統計を持ちます。

# フィールド

  * `sym::Symbol`: 変数の名前
  * `mean::T`: 平均
  * `var::T`: 分散
  * `min::T`: 最小値
  * `max::T`: 最大値
