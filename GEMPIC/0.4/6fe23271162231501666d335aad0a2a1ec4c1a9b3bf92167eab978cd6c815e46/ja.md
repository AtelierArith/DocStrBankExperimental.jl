```
compute_rhs_from_function(solver, func, coefs_dofs)
```

与えられた関数 f と指定された次数の周期スプラインに対して FEM 右辺を計算します。その成分は $\int f N_i dx$ であり、ここで $N_i$ は $x_i$ から始まる B-スプラインです。

  * solver :: マクスウェルソルバー
  * func : 関数
  * coefs_dofs[:]  : 有限要素右辺

```
