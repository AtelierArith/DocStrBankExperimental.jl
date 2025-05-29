```
AmhCopula
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
AmhCopula(n::Int, θ::Real)
```

The Ali-Mikhail-Haq copula parameterized by θ, domain: θ ∈ (0, 1) for n > 2 and  θ ∈ [-1, 1] for n = 2.

Constructor

```
AmhCopula(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero. Such correlation must be grater than zero and limited from above due to the θ domain.             - Spearman correlation must be in range (0, 0.5)             - Kendall correlation must be in range (0, 1/3)

```jldoctest
julia> AmhCopula(4, .3)
AmhCopula(4, 0.3)

julia> AmhCopula(4, .3, KendallCorrelation)
AmhCopula(4, 0.9999)

```
