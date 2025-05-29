```
deviance(m::GeneralizedLinearMixedModel{T}, nAGQ=1)::T where {T}
```

Return the deviance of `m` evaluated by the Laplace approximation (`nAGQ=1`) or `nAGQ`-point adaptive Gauss-Hermite quadrature.

If the distribution `D` does not have a scale parameter the Laplace approximation is the squared length of the conditional modes, $u$, plus the determinant of $Λ'Z'WZΛ + I$, plus the sum of the squared deviance residuals.
