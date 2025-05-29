```Julia
angulararea(U::UnitSystem,S::UnitSystem) = area(U,S)/solidangle(U,S)
angulararea(v::Real,U::UnitSystem,S::UnitSystem) = v/angulararea(U,S)
```

二次元形状の範囲または `area` (m²)、単位変換係数。

```Julia
julia> angulararea(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000005

julia> angulararea(English,Metric) # m²⋅ft⁻²
0.09290304
```
