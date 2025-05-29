```Julia
rayl(U::UnitSystem) = specificimpedance(𝟏,U,Metric)
specificimpedance : [FL⁻³T], [FL⁻³T], [ML⁻²T⁻¹], [ML⁻²T⁻¹], [ML⁻²T⁻¹]
FL⁻³T⋅(𝘩⁻¹R∞⁻⁴α⁸τ⁻³2⁻⁴ = 2.1085780876(26) × 10⁻¹⁶) [ħ⁻³𝘤⁴mₑ⁴ϕ⁻³g₀⁻⁴] 統一

Metric unit of `specificimpedance` (kg⋅m⁻²⋅s⁻¹ or lb⋅s⋅ft⁻³).

```

Julia julia> rayl(Metric) # kg⋅m⁻²⋅s⁻¹ 𝟏 = 1.0 [kg⋅m⁻²s⁻¹] メトリック

julia> rayl(CGS) # g⋅cm⁻²⋅s⁻¹ 2⁻¹5⁻¹ = 0.1 [g⋅cm⁻²s⁻¹] ガウス

julia> rayl(English) # lb⋅s⋅ft⁻³ g₀⁻¹ft³lb⁻¹ = 0.00636588035426416 [lbf⋅ft⁻³s] 英語 ```
