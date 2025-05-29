```Julia
area(U::UnitSystem,S::UnitSystem) = length(U,S)^2
area(v::Real,U::UnitSystem,S::UnitSystem) = v/area(U,S)
```

二次元形状の範囲または `area` (m²)、単位変換係数。

```Julia
julia> area(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000005

julia> area(English,Metric) # m²⋅ft⁻²
0.09290304

julia> area(Survey,English) # ft²⋅ftUS⁻²
1.0000040000119998
```
