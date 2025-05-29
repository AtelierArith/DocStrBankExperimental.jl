```
jacobi!(x, A::SparseMatrixCSC, b; maxiter=10) -> x
```

Performs exactly `maxiter` Jacobi iterations.

Allocates a temporary vector and precomputes the diagonal indices.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
