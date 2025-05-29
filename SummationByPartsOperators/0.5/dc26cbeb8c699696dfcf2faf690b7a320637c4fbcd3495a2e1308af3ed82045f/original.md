```
integrate_boundary([func = identity,] u, D::MultidimensionalMatrixDerivativeOperator, dim)
```

Map the function `func` to the coefficients `u` and integrate along the boundary in direction `dim` with respect to the surface quadrature rule associated with the [`MultidimensionalMatrixDerivativeOperator`](@ref) `D`.
