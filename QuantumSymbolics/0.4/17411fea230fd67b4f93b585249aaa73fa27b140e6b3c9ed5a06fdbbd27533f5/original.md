```
express(s, repr::AbstractRepresentation=QuantumOpticsRepr()[, use::AbstractUse])
```

The main interface for expressing symbolic quantum objects in various representations.

```jldoctest
julia> express(X1)
Ket(dim=2)
  basis: Spin(1/2)
 0.7071067811865475 + 0.0im
 0.7071067811865475 + 0.0im

julia> express(X1, CliffordRepr())
𝒟ℯ𝓈𝓉𝒶𝒷
+ Z
𝒮𝓉𝒶𝒷
+ X

julia> express(QuantumSymbolics.X)
Operator(dim=2x2)
  basis: Spin(1/2)
      ⋅       1.0 + 0.0im
 1.0 + 0.0im       ⋅

julia> express(QuantumSymbolics.X, CliffordRepr(), UseAsOperation())
sX

julia> express(QuantumSymbolics.X, CliffordRepr(), UseAsObservable())
+ X
```
