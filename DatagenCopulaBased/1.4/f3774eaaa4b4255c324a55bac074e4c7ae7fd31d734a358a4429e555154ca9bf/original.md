```
DoubleNestedGumbelCopula
```

Fields:

  * children::Vector{Nested _Gumbel _cop}  vector of children copulas
  * θ::Real - parameter of parent copula, domain θ ∈ [1,∞).

Constructor

```
Double_Nested_Gumbel _cop(children::Vector{NestedGumbelCopula}, θ::Real)
```

requires sufficient nesting condition for θ and child copulas.

Constructor

```
Doulbe_NestedGumbelCopula(children::Vector{NestedGumbelCopula}, θ::Real, cor::Type{<:CorrelationType})
```

For computing copula parameter from expected correlation use empty type cor::Type{<:CorrelationType} where SpearmanCorrelation <:CorrelationType and KendallCorrelation<:CorrelationType. If used cor put expected correlation in the place of θ  in the constructor. The copula parameter will be computed then. The correlation must be greater than zero.

```jldoctest

julia> a = GumbelCopula(2, 5.)
GumbelCopula(2, 5.0)

julia> b = GumbelCopula(2, 6.)
GumbelCopula(2, 6.0)

julia> c = GumbelCopula(2, 5.5)
GumbelCopula(2, 5.5)

julia> p1 = NestedGumbelCopula([a,b], 1, 2.)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 6.0)], 1, 2.0)

julia> p2 = NestedGumbelCopula([c], 2, 2.1)
NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.5)], 2, 2.1)

julia> DoubleNestedGumbelCopula([p1, p2], 1.5)
DoubleNestedGumbelCopula(NestedGumbelCopula[NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.0), GumbelCopula(2, 6.0)], 1, 2.0), NestedGumbelCopula(GumbelCopula[GumbelCopula(2, 5.5)], 2, 2.1)], 1.5)
```
