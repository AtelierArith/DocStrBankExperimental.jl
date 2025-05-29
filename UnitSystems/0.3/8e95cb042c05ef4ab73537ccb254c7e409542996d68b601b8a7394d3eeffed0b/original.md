```Julia
density(U::UnitSystem,S::UnitSystem) = mass(U,S)/volume(U,S)
density(v::Real,U::UnitSystem,S::UnitSystem) = v/density(U,S)
```

Specific mass or `mass` per `volume` or `density` (kg⋅m⁻³), unit conversion factor.

```Julia
julia> density(CGS,Metric) # kg⋅cm³⋅g⁻¹⋅m⁻³
999.9999999999994

julia> density(CGS,Brtish) # slug⋅cm³⋅g⁻¹⋅ft⁻³
1.940320331979716

julia> density(English,Metric) # kg⋅ft³⋅lb⁻¹⋅m⁻³
16.018463373960138
```
