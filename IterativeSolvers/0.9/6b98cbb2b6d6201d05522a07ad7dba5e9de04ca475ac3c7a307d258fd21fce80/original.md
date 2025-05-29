```
gauss_seidel!(x, A::AbstractMatrix, b; maxiter=10) -> x
```

Performs exactly `maxiter` Gauss-Seidel iterations.

Works fully in-place and traverses `A` columnwise.

Throws `LinearAlgebra.SingularException` when the diagonal has a zero. This check is performed once beforehand.
