```
FrankCopula
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
FrankCopula(n::Int, θ::Real)
```

The Frank n variate copula parameterized by θ::Real. Domain: θ ∈ (0, ∞) for n > 2 and θ ∈ (-∞, 0) ∪ (0, ∞) for n = 2, supported for n::Int ≧ 2.

Constructor

```
FrankCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest
julia> FrankCopula(2, -5.)
FrankCopula(2, -5.0)

julia> FrankCopula(4, .3)
FrankCopula(4, 0.3)
```
