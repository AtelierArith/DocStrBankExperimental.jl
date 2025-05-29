```
ssor!(x, A::AbstractMatrix, b, ω::Real; maxiter=10) -> x
```

Performs exactly `maxiter` SSOR iterations with relaxation parameter `ω`. Each iteration is basically a forward *and* backward sweep of SOR.

Allocates a single temporary vector and traverses `A` columnwise.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
