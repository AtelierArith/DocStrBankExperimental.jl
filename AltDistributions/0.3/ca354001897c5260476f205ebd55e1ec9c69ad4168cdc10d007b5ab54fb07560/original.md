```julia
StdCorrFactor(σ, F)

```

A factor `L` of a covariance matrix `Σ = LL'` given as `L = Diagonal(σ) * F`. Can be used in place of `L`, without performing the multiplication.
