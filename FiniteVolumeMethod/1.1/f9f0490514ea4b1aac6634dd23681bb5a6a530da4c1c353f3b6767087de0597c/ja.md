```
pl_interpolate(prob, T, u, x, y)
```

`prob <: AbstractFVMProblem`、点 `(x, y)` を含む三角形 `T`、および `prob` の対応するノードでの関数値のセット `u` が与えられたとき、線形補間を用いて点 `(x, y)` での解を補間します。
