```julia
mutable struct ChainsTune
```

データに対するチェーンの数の調整情報を保持します。

# フィールド

  * `coverage::Float64`: チェーンの数/データポイントの提案されたカバレッジ。
  * `threshold::Float64`: 再サンプリングのための閾値、0.0と1.0の間。
  * `Nchains::Int64`: チェーンの数。
  * `Ndata::Int64`: データポイントの数。
