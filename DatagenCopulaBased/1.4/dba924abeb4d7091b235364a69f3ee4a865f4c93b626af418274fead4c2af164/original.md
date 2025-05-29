```
GaussianCopula
```

Gaussian copula

Fields:

  * Σ - the correlation matrix must be symmetric, positively defined and with ones on diagonal

Constructor

```
GaussianCopula(Σ::Matrix{T}) where T <: Real
```

```jldoctest

julia> GaussianCopula([1. 0.5; 0.5 1.])
GaussianCopula([1.0 0.5; 0.5 1.0])

```
