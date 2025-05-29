```
gauss_seidel!(x, A::SparseMatrixCSC, b; maxiter=10) -> x
```

Performs exactly `maxiter` Gauss-Seidel iterations.

Works fully in-place, but precomputes the diagonal indices.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
