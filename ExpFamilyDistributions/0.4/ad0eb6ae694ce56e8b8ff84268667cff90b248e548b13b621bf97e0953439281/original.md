```
kldiv(q::T, p::T) where T<:ExpFamilyDistribution
```

Compute the KL-divergence between two distributions of the same type (i.e. `kldiv(Normal, Normal)`, `kldiv(Dirichlet, Dirichlet)`, ...)
