```Julia
footpound(U::UnitSystem) = poundforce(U)*foot(U)
```

重力および工学システムにおけるエネルギーの英単位（Jまたはlb⋅ft）。

```Julia
julia> footpound(Metric) # J
1.3558179483314006

julia> footpound(CGS) # erg
1.3558179483314004e7

julia> footpound(British) # lb⋅ft
1
```
