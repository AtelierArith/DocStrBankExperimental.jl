```Julia
footpound(U::UnitSystem) = poundforce(U)*foot(U)
```

English unit of `energy` in gravitational and engineering systems (J or lb⋅ft).

```Julia
julia> footpound(Metric) # J
1.3558179483314006

julia> footpound(CGS) # erg
1.3558179483314004e7

julia> footpound(British) # lb⋅ft
1
```
