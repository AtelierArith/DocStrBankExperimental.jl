```Julia
area(U::UnitSystem,S::UnitSystem) = length(U,S)^2
area(v::Real,U::UnitSystem,S::UnitSystem) = v/area(U,S)
```

Extent of two-dimensional shape or `area` (m²), unit conversion factor.

```Julia
julia> area(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000005

julia> area(English,Metric) # m²⋅ft⁻²
0.09290304

julia> area(Survey,English) # ft²⋅ftUS⁻²
1.0000040000119998
```
