```
ssor!(x, A::SparseMatrixCSC, b, ω::Real; maxiter=10)
```

Performs exactly `maxiter` SSOR iterations with relaxation parameter `ω`. Each iteration is basically a forward *and* backward sweep of SOR.

Allocates a temporary vector and precomputes the diagonal indices.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
