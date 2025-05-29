```
coordoperator(sys, crd)
coordoperator(basis, crd)
coordoperator(lat[, internal], crd)
```

与えられた格子の座標演算子を生成します。

## 引数

  * `sys`: 座標演算子を生成するための `System`。
  * `basis`: 座標演算子を生成するための一粒子 `Basis`。
  * `lat`: 座標演算子を生成するための格子。
  * `internal`: 内部自由度のための基底。
  * `crd`: 演算子を生成するための座標。座標インデックスを表す整数（例：`1` は x、`2` は y など）またはシンボル（例：`:x`、`:y` など）でなければなりません。
