```
NestedFrankCopula
```

Fields:

  * children::Vector{FrankCopula}  vector of children copulas
  * m::Int ≧ 0 - number of additional marginals modeled by the parent copula only
  * θ::Real - parameter of parent copula, domain θ ∈ (0,∞).

Nested Frank copula: C _θ(C _ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C _ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ). If m > 0, the last m variables will be modeled by the parent copula only.

Constructor

```
NestedFrankCopula(children::Vector{FrankCopula}, m::Int, θ::Real)
```

Let ϕ be the vector of parameter of children copula, sufficient nesting condition requires θ <= minimum(ϕ)

Constructor

```
NestedFrankCopula(children::Vector{Frank_ cop}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctests

julia> a = FrankCopula(2, 5.)
FrankCopula(2, 5.0)

julia> NestedFrankCopula([a, a], 2, 0.1)
NestedFrankCopula(FrankCopula[FrankCopula(2, 5.0), FrankCopula(2, 5.0)], 2, 0.1)
```
