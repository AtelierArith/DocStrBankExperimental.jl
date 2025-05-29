```Julia
compressibility : [F⁻¹L²], [F⁻¹L²], [M⁻¹LT²], [M⁻¹LT²], [M⁻¹LT²]
compressibility(U::UnitSystem,S::UnitSystem) = 1/pressure(U,S)
compressibility(v::Real,U::UnitSystem,S::UnitSystem) = v/compressibility(U,S)
F⁻¹L² [ħ³𝘤⁻⁵mₑ⁻⁴ϕ³g₀⁴] Unified
```

Relative volume change or `compressibility` (Pa⁻¹), unit conversion factor.

```Julia
julia> compressibility(CGS,Metric) # Ba⋅Pa⁻¹
2⋅5 = 10.0 [Pa⁻¹]/[Ba⁻¹] Gauss -> Metric

julia> compressibility(English,Metric) # lb⋅ft⁻²⋅Pa⁻¹
g₀⁻¹ft²lb⁻¹ = 0.02088543423315013 [Pa⁻¹]/[lbf⁻¹ft²] English -> Metric

julia> compressibility(Metric,IPS) # Pa⋅psi⁻¹
g₀⋅ft⁻²lb⋅2⁴3² = 6894.75729316836 [lb⁻¹in²]/[Pa⁻¹] Metric -> IPS
```
