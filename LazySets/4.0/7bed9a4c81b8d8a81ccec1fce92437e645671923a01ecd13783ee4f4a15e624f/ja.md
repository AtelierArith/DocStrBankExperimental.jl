```
ProjectionSparseMatrixExp{N, MN1<:AbstractSparseMatrix{N},
                             MN2<:AbstractSparseMatrix{N},
                             MN3<:AbstractSparseMatrix{N}}
```

スパース行列指数の射影を表す型、すなわち、与えられたスパース行列 $M$ に対して $L⋅\exp(M)⋅R$ です。

### フィールド

  * `L` – 左乗算行列
  * `E` – スパース行列指数
  * `R` – 右乗算行列
