```
λ, V = eigs(A::Operator, n::Integer; tolerance::Float64=100eps())
```

Compute the eigenvalues and eigenvectors of the operator `A`. This is done in the following way:

  * Truncate `A` into an `n×n` matrix `A₁`.
  * Compute eigenvalues and eigenvectors of `A₁`.
  * Filter for those eigenvectors of `A₁` that are approximately eigenvectors

of `A` as well. The `tolerance` argument controls, which eigenvectors of the approximation are kept.
