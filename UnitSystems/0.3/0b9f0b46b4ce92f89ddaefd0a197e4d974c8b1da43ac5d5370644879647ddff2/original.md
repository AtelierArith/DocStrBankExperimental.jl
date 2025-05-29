```Julia
joule(U::UnitSystem) = energy(𝟏,U,Metric)
```

Metric unit of `energy` (J or lb⋅ft).

```Julia
julia> joule(Metric) # J
1

julia> joule(CGS) # erg
1.0e7

julia> joule(British) # lb⋅ft
0.7375621492772654
```
