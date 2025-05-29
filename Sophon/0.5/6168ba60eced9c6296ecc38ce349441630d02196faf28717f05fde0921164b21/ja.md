```
NonAdaptiveTraining(pde_weights=1, bcs_weights=pde_weights)
```

損失関数の固定重み。

## 引数

  * `pde_weights`: PDE損失関数の重み。単一の数値が与えられた場合、すべてのPDE損失関数に使用されます。
  * `bcs_weights`: 境界条件損失関数の重み。単一の数値が与えられた場合、すべての境界条件損失関数に使用されます。
