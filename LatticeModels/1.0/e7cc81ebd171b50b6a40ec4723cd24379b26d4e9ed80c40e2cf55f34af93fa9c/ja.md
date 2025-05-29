```
tightbinding_hamiltonian([T, ]sys[, args...; t1=1, t2=0, t3=0, field, auto_pbc_field])
tightbinding_hamiltonian([T, ]lat[, internal, args...; t1=1, t2=0, t3=0, field, auto_pbc_field])
```

与えられた系のためのタイトバインディングハミルトニアンを構築します。

## 引数

  * `T`: ハミルトニアンの要素タイプ。デフォルトは `ComplexF64` です。
  * `sys`: ハミルトニアンが構築される `System`。
  * `lat`: ハミルトニアンが構築される格子。
  * `internal`: 内部自由度のための基底。

他のすべての引数はハミルトニアンの項として解釈され、`construct_hamiltonian` に渡されます。

## キーワード引数

  * `t1`, `t2`, `t3`: 最近接、次最近接、次次最近接の隣接点のためのホッピング振幅。
  * `field`: ボンド演算子に使用するゲージ場。デフォルトは `NoField()` です。
  * `auto_pbc_field`: 格子の周期境界条件に自動的にフィールドを適応させるかどうか。デフォルトは `true` です。
