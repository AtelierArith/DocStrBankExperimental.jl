```
SparseVariationalApproximation(fz::FiniteGP, q::AbstractMvNormal)
```

Packages the prior over the pseudo-points `fz`, and the approximate posterior at the pseudo-points, which is `mean(fz) + cholesky(cov(fz)).L * ε`, `ε ∼ q`.

Shorthand for

```julia
SparseVariationalApproximation(NonCentered(), fz, q)
```
