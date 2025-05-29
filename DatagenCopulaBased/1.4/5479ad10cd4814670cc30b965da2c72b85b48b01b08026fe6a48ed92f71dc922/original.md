```
GumbelCopula
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
    GumbelCopula(n::Int, θ::Real)
```

The Gumbel n variate copula is parameterized by θ::Real ∈ [1, ∞), supported for n::Int ≧ 2.

Constructor

```
GumbelCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest

julia> GumbelCopula(4, 3.)
GumbelCopula(4, 3.0)

julia> GumbelCopula(4, .75, KendallCorrelation)
GumbelCopula(4, 4.0)
```
