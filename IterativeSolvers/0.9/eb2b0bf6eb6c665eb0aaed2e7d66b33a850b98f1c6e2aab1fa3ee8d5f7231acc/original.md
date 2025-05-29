```
jacobi!(x, A::AbstractMatrix, b; maxiter=10) -> x
```

Performs exactly `maxiter` Jacobi iterations.

Allocates a single temporary vector and traverses `A` columnwise.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
