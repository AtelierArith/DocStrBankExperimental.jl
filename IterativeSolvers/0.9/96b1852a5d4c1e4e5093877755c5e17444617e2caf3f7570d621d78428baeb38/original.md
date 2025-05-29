```
sor!(x, A::SparseMatrixCSC, b, ω::Real; maxiter=10)
```

Performs exactly `maxiter` SOR iterations with relaxation parameter `ω`.

Allocates a temporary vector and precomputes the diagonal indices.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
