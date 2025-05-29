```
integrate_boundary([func = identity,] u, D::MultidimensionalMatrixDerivativeOperator, dim)
```

関数 `func` を係数 `u` にマッピングし、[`MultidimensionalMatrixDerivativeOperator`](@ref) `D` に関連する表面ガウス則に従って、次元 `dim` に沿って境界で積分します。
