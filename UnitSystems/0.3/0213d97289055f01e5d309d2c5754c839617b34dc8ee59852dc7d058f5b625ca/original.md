```Julia
volumeflow(U::UnitSystem,S::UnitSystem) = area(U,S)*speed(U,S)
volumeflow(v::Real,U::UnitSystem,S::UnitSystem) = v/volumeflow(U,S)
```

Volumetric flow rate or `volumeflow` (m³⋅s⁻¹), unit conversion factor.

```Julia
julia> volumeflow(CGS,Metric) # m³⋅cm⁻³
1.0000000000000006e-6

julia> volumeflow(English,Metric) # m³⋅ft⁻³
0.028316846592000004

julia> volumeflow(Survey,English) # ft³⋅ftUS⁻³
1.0000060000239999
```
