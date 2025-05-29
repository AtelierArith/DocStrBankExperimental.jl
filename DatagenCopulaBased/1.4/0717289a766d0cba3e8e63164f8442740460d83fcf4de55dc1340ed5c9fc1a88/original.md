```
NestedGumbelCopula
```

Fields:

  * children::Vector{GumbelCopula}  vector of children copulas
  * m::Int ≧ 0 - number of additional marginals modeled by the parent copula only
  * θ::Real - parameter of parent copula, domain θ ∈ [1,∞).

Nested Gumbel copula: C _θ(C _ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C _ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ). If m > 0, the last m variables will be modeled by the parent copula only.

Constructor

```
NestedGumbelCopula(children::Vector{GumbelCopula}, m::Int, θ::Real)
```

Let ϕ be the vector of parameter of children copula, sufficient nesting condition requires θ <= minimum(ϕ)

Constructor

```
NestedGumbelCopula(children::Vector{GumbelCopula}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest

julia> a = GumbelCopula(2, 5.)
GumbelCopula(2, 5.0)

julia> NestedGumbelCopula([a, a], 2, 2.1)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 5.0)], 2, 2.1)
```
