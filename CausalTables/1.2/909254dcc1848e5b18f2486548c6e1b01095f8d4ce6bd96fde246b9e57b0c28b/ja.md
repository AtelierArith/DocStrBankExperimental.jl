```
confounders(o::CausalTable, x::Symbol, y::Symbol)
```

特定の変数ペア (x,y) の共通原因を指定された `CausalTable` オブジェクトから選択します。

# 引数

  * `o::CausalTable`: 混乱因子を抽出するための `CausalTable` オブジェクト。
  * `x::Symbol`, `y::Symbol`: 混乱因子を選択すべき2つの変数。

# 戻り値

x と y の混乱因子のみを含む新しい `CausalTable`。
