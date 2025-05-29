```Julia
compliance : [M⁻¹T²], [F⁻¹L], [M⁻¹T²], [M⁻¹T²], [M⁻¹T²]
compliance(U::UnitSystem,S::UnitSystem) = time(U,S)^2/mass(U,S)
compliance(v::Real,U::UnitSystem,S::UnitSystem) = v/compliance(U,S)
M⁻¹T² [ħ²𝘤⁻⁴mₑ⁻³ϕ²g₀²] Unified
```

Acoustic `compliance` is reciprocal of `fluence` (m⋅N⁻¹, m³⋅Pa⁻¹), unit conversion factor.

```Julia
julia> compliance(CGS,Metric) # kg⋅g⁻¹
2³5³ = 1000.0 [kg⁻¹]/[g⁻¹] Gauss -> Metric

julia> compliance(CGS,English) # slug⋅g⁻¹
lb⋅2³5³ = 453.59237 [lbm⁻¹]/[g⁻¹] Gauss -> English

julia> compliance(English,Metric) # kg⋅lb⁻¹
lb⁻¹ = 2.2046226218487757 [kg⁻¹]/[lbm⁻¹] English -> Metric
```
