```Julia
diffusivity(U::UnitSystem,S::UnitSystem) = speed(U,S)*length(U,S)
diffusivity(v::Real,U::UnitSystem,S::UnitSystem) = v/diffusivity(U,S)
```

Thermal `diffusivity` or kinematic viscostiy (m²⋅s⁻¹), unit conversion factor.

```Julia
julia> diffusivity(CGS,Metric) # m²⋅cm⁻²
0.00010000000000000002

julia> diffusivity(English,Metric) # m²⋅ft⁻²
0.09290304

julia> diffusivity(Survey,English) # ft²⋅ftUS⁻²
1.0000040000119998
```
