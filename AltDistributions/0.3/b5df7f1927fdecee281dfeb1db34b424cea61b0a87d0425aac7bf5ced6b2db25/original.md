```julia
AltMvNormal(μ, Σ)

```

Multivariate normal distribution with mean `μ` and covariance matrix `Σ`, which can be an abstract matrix (eg a factorization) or `I`. If `Σ` is not symetric because of numerical error, wrap in `LinearAlgebra.Symmetric`.

Use the `AltMvNormal(Val(:L), μ, L)` constructor for using `LL'=Σ` directly.

Also, see [`StdCorrFactor`](@ref) for formulating `L` from standard deviations and a Cholesky factor of a *correlation* matrix:

```julia
AltMvNormal(Val(:L), μ, StdCorrFactor(σ, S))
```
