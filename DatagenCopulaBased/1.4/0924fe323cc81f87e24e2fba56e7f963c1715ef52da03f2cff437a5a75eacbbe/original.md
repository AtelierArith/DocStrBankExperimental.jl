```
AmhCopulaRev
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
AmhCopulaRev(n::Int, θ::Real)
```

The reversed Ali-Mikhail-Haq copula parametrized by θ, i.e. such that the output is 1 .- u, where u is modelled by the corresponding AMH copula. Domain: θ ∈ (0, 1) for n > 2 and  θ ∈ [-1, 1] for n = 2.

Constructor

```
AmhCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero. Such correlation must be grater than zero and limited from above due to the θ domain.               - Spearman correlation must be in range (0, 0.5)               -  Kendall correlation must be in range (0, 1/3)

```jldoctest
julia> AmhCopulaRev(4, .3)
AmhCopulaRev(4, 0.3)
```
