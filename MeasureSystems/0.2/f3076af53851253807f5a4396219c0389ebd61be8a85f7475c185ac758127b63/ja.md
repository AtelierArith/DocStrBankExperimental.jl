```Julia
volumeflow : [L³T⁻¹], [L³T⁻¹], [L³T⁻¹], [L³T⁻¹], [L³T⁻¹]
volumeflow(U::UnitSystem,S::UnitSystem) = area(U,S)*speed(U,S)
volumeflow(v::Real,U::UnitSystem,S::UnitSystem) = v/volumeflow(U,S)
L³T⁻¹ [ħ²𝘤⁻¹mₑ⁻²ϕ²g₀²] 統一

体積流量または `volumeflow` (m³⋅s⁻¹)、単位変換係数。

```

Julia julia> volumeflow(CGS,Metric) # m³⋅cm⁻³ 2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [m³]/[mL] ガウス -> メトリック

julia> volumeflow(English,Metric) # m³⋅ft⁻³ ft³ = 0.028316846592000004 [m³]/[ft³] 英語 -> メトリック

julia> volumeflow(Survey,English) # ft³⋅ftUS⁻³ ft⁻³ftUS³ = 1.0000060000239996 [ft³]/[ft³] サーベイ -> 英語 ```
