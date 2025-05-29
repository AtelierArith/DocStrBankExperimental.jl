```
lobpcg!(iterator::LOBPCGIterator; kwargs...) -> results
```

# 引数

  * `iterator::LOBPCGIterator`: LOBPCGアルゴリズムに必要なすべての変数を持つ構造体。

## キーワード

  * `not_zeros`: デフォルトは `false`。`true` の場合、初期リッツベクトルはすべてゼロの列を持たないと仮定されます。
  * `log::Bool`: デフォルトは `false`；`true` の場合、`results.trace` は反復状態を保存します；`false` の場合、`results.trace` は空になります；
  * `maxiter`: 最大反復回数；デフォルトは200；
  * `tol::Real`: 残差ベクトルのノルムが下回るべき許容誤差。

# 出力

  * `results`: `LOBPCGResults` 構造体。`r.λ` と `r.X` は固有値と固有ベクトルを保存します。
