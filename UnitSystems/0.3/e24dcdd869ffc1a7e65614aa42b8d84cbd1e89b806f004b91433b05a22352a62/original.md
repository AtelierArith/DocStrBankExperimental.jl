```Julia
angulararea(U::UnitSystem,S::UnitSystem) = area(U,S)/solidangle(U,S)
angulararea(v::Real,U::UnitSystem,S::UnitSystem) = v/angulararea(U,S)
```

Extent of two-dimensional shape or `area` (m²), unit conversion factor.

```Julia
julia> angulararea(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000005

julia> angulararea(English,Metric) # m²⋅ft⁻²
0.09290304
```
