```
NestedClaytonCopula
```

Fields:

  * children::Vector{ClaytonCopula}  vector of children copulas
  * m::Int ≧ 0 - number of additional marginals modeled by the parent copula only
  * θ::Real - parameter of parent copula, domain θ > 0.

Nested Clayton copula: C*θ(C*ϕ₁(u₁₁, ..., u₁,ₙ₁), ..., C_ϕₖ(uₖ₁, ..., uₖ,ₙₖ), u₁ , ... uₘ). If m > 0, the last m variables will be modeled by the parent copula only.

Constructor

```
NestedClaytonCopula(children::Vector{ClaytonCopula}, m::Int, θ::Real)
```

Let ϕ be the vector of parameter of children copula, sufficient nesting condition requires θ <= minimum(ϕ)

Constructor

```
NestedClaytonCopula(children::Vector{ClaytonCopula}, m::Int, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest
julia> a = ClaytonCopula(2, 2.)
ClaytonCopula(2, 2.0)

julia> NestedClaytonCopula([a], 2, 0.5)
NestedClaytonCopula(ClaytonCopula[ClaytonCopula(2, 2.0)], 2, 0.5)

julia> NestedClaytonCopula([a, a], 2, 0.5)
NestedClaytonCopula(ClaytonCopula[ClaytonCopula(2, 2.0), ClaytonCopula(2, 2.0)], 2, 0.5)

```
