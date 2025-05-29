```
ClaytonCopulaRev
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
ClaytonCopulaRev(n::Int, θ::Real)
```

The reversed Clayton copula parameterized by θ::Real (reversed means u → 1 .- u). Domain: θ ∈ (0, ∞) for n > 2 and θ ∈ [-1, 0) ∪ (0, ∞) for n = 2, supported for n::Int ≧ 2.

Constructor

```
ClaytonCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest

julia> ClaytonCopulaRev(4, 3.)
ClaytonCopulaRev(4, 3.0)

julia> ClaytonCopulaRev(4, 0.9, SpearmanCorrelation)
ClaytonCopulaRev(4, 5.5595567742323775)

```
