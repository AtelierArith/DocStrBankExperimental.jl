```Julia
admittance : [F⁻¹L⁵T⁻¹], [F⁻¹L⁵T⁻¹], [M⁻¹L⁴T], [M⁻¹L⁴T], [M⁻¹L⁴T]
admittance(U::UnitSystem,S::UnitSystem) = area(U,S)/specificimpedance(U,S)
admittance(v::Real,U::UnitSystem,S::UnitSystem) = v/admittance(U,S)
F⁻¹L⁵T⁻¹ [ħ⁵𝘤⁻⁶mₑ⁻⁶ϕ⁵g₀⁶] Unified
```

Acoustic `admittance` (m²⋅Rayl⁻¹, m³⋅s⁻¹⋅Pa⁻¹, m⁴⋅s⋅kg⁻¹), unit conversion factor.

```Julia
julia> admittance(CGS,Metric) # Ba⋅m³⋅cm⁻³⋅Pa⁻¹
2⁻⁵5⁻⁵ = 1.0×10⁻⁵ [kg⁻¹m⁴s²]/[g⁻¹cm⁴s²] Gauss -> Metric

julia> admittance(English,Metric) # lb⋅m³⋅ft⁻⁵⋅Pa⁻¹
g₀⁻¹ft⁵lb⁻¹ = 0.0005914096371874175 [kg⁻¹m⁴s²]/[lbf⁻¹ft⁵] English -> Metric
```
