```
Jx = jac_op_residual!(nls, rows, cols, vals, Jv, Jtv)
```

与えられた `(rows, cols, vals)` による残差のヤコビアン $J(x)$ を線形演算子形式で計算します。ベクトル `Jv` と `Jtv` は操作のための事前割り当てされたストレージとして使用されます。
