```
GumbelCopulaRev
```

Fields:

  * n::Int - number of marginals
  * θ::Real - parameter

Constructor

```
GumbelCopulaRev(n::Int, θ::Real)
```

The reversed Gumbel copula (reversed means u → 1 .- u), parameterized by θ::Real ∈ [1, ∞), supported for n::Int ≧ 2.

Constructor

```
GumbelCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest
julia> c = GumbelCopulaRev(4, .75, KendallCorrelation)
GumbelCopulaRev(4, 4.0)

julia> Random.seed!(43);

julia> simulate_copula(2, c)
2×4 Array{Float64,2}:
 0.963524   0.872108  0.816626  0.783637
 0.0954475  0.138451  0.13593   0.0678172
```
