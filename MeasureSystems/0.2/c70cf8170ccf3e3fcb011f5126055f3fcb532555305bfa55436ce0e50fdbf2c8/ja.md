```Julia
compliance : [M⁻¹T²], [F⁻¹L], [M⁻¹T²], [M⁻¹T²], [M⁻¹T²]
compliance(U::UnitSystem,S::UnitSystem) = time(U,S)^2/mass(U,S)
compliance(v::Real,U::UnitSystem,S::UnitSystem) = v/compliance(U,S)
M⁻¹T² [ħ²𝘤⁻⁴mₑ⁻³ϕ²g₀²] 統一

音響の `compliance` は `fluence` の逆数です (m⋅N⁻¹, m³⋅Pa⁻¹)、単位換算係数。

```

Julia julia> compliance(CGS,Metric) # kg⋅g⁻¹ 2³5³ = 1000.0 [kg⁻¹]/[g⁻¹] ガウス -> メトリック

julia> compliance(CGS,English) # slug⋅g⁻¹ lb⋅2³5³ = 453.59237 [lbm⁻¹]/[g⁻¹] ガウス -> 英語

julia> compliance(English,Metric) # kg⋅lb⁻¹ lb⁻¹ = 2.2046226218487757 [kg⁻¹]/[lbm⁻¹] 英語 -> メトリック ```
