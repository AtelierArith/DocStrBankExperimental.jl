```
HierarchicalGumbelCopula
```

Fields:

  * n::Int - number of marginals
  * θ::Vector{Real} - vector of parameters, must be decreasing  and θ[end] ≧ 1, for the

sufficient nesting condition to be fulfilled.

The hierarchically nested Gumbel copula C*θₙ₋₁(C*θₙ₋₂( ... C*θ₂(C*θ₁(u₁, u₂), u₃)...uₙ₋₁) uₙ)

Constructor

```
HierarchicalGumbelCopula(θ::Vector{Real})
```

Constructor

```
HierarchicalGumbelCopula(ρ::Vector{Real}, cor::Type{<:CorrelationType})
```

For computing copula parameters from expected correlations use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlations in the place of θ  in the constructor. The copula parameters will be computed then. The correlation must be greater than zero.

```jldoctest

julia> c = HierarchicalGumbelCopula([5., 4., 3.])
HierarchicalGumbelCopula(4, [5.0, 4.0, 3.0])

julia> c = HierarchicalGumbelCopula([0.95, 0.5, 0.05], KendallCorrelation)
HierarchicalGumbelCopula(4, [19.999999999999982, 2.0, 1.0526315789473684])
```
