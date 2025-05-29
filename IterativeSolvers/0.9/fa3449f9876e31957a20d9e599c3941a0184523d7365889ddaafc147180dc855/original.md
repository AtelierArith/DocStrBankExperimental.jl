```
sor!(x, A::AbstractMatrix, b, ω::Real; maxiter=10) -> x
```

Performs exactly `maxiter` SOR iterations with relaxation parameter `ω`.

Allocates a single temporary vector and traverses `A` columnwise.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
