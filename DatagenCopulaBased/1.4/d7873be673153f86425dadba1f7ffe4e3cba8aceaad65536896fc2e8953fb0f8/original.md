```
StudentCopula
```

t-Student copula

fields

  * Σ::Matrix{Real} - the correlation matrix must be symmetric, positively defined and with ones on diagonal
  * ν::Int - the parameter n.o. degrees of freedom we require ν > 0

Constructor:

```
StudentCopula(Σ::Matrix{Real}, ν::Int)
```

```jldoctest

julia> StudentCopula([1. 0.5; 0.5 1.], 4)
StudentCopula([1.0 0.5; 0.5 1.0], 4)

```
