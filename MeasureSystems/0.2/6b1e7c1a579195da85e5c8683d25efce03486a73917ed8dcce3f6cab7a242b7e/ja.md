```Julia
特異性 : [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹], [L³T⁻¹N⁻¹]
特異性(U::UnitSystem,S::UnitSystem) = volume(U,S)/molaramount(U,S)/time(U,S)
特異性(v::Real,U::UnitSystem,S::UnitSystem) = v/特異性(U,S)
L³T⁻¹N⁻¹ [ħ²𝘤⁻¹mₑ⁻³Mᵤ⋅ϕ²g₀²] 統一

触媒効率または `volume` per `mole` per `time` (m³⋅mol⁻¹⋅s⁻¹)、単位換算係数。

```

Julia julia> 特異性(CGS,Metric) # m³⋅cm⁻³ 2⁻⁶5⁻⁶ = 1.0×10⁻⁶ [m³]/[mL] ガウス -> メトリック

julia> 特異性(English,Metric) # m³⋅lb-mol⋅mol⁻¹⋅ft⁻³ ft³lb⁻¹2⁻³5⁻³ = 6.242796057614462×10⁻⁵ [m³mol⁻¹]/[ft³lb-mol⁻¹] 英語 -> メトリック ```
