```
NestedAmhCopula
```

Nested Ali-Mikhail-Haq copula, fields:

  * children::Vector{AMH _cop}  vector of children copulas
  * m::Int ≧ 0 - number of additional marginals modeled by the parent copula only
  * θ::Real - parameter of parent copula, domain θ ∈ (0,1).

Nested Ali-Mikhail-Haq copula: C _θ(C _ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C _ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ). If m > 0, the last m variables will be modeled by the parent copula only.

Constructor

```
NestedAmhCopula(children::Vector{AmhCopula}, m::Int, θ::Real)
```

Let ϕ be the vector of parameter of children copula, sufficient nesting condition requires θ <= minimum(ϕ)

Constructor

```
NestedAmhCopula(children::Vector{AmhCopula}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest

julia> a = AmhCopula(2, .2)
AmhCopula(2, 0.2)

julia> NestedAmhCopula([a, a], 2, 0.1)
NestedAmhCopula(AmhCopula[AmhCopula(2, 0.2), AmhCopula(2, 0.2)], 2, 0.1)

```
