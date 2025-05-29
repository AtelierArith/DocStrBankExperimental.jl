```Julia
etendue(U::UnitSystem,S::UnitSystem) = area(U,S)*solidangle(U,S)
etendue(v::Real,U::UnitSystem,S::UnitSystem) = v/etendue(U,S)
```

エタンデュ（Etendue）または `area` と `solidangle` の積（m², ft²）、単位変換係数。

```Julia
julia> etendue(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000005

julia> etendue(English,Metric) # m²⋅ft⁻²
0.09290304
```
