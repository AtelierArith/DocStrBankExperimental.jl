```Julia
erg(U::UnitSystem) = energy(𝟏,U,Gauss)
```

歴史的な単位の `energy` (J または lb⋅ft)。

```Julia
julia> erg(Metric) # J
1.0e-7

julia> erg(CGS) # erg
1

julia> erg(British) # lb⋅ft
7.375621492772654e-8
```
