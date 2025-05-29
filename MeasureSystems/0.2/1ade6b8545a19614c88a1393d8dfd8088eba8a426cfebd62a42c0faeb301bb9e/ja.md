```Julia
langley(U::UnitSystem) = calorie(U)/(centi*meter(U))^2
fluence : [FL⁻¹], [FL⁻¹], [MT⁻²], [MT⁻²], [MT⁻²]
FL⁻¹⋅(𝘩⁻¹𝘤⁻¹R∞⁻³α⁶Ωᵢₜ⁻¹Vᵢₜ²τ⁻²2³3²5⁵43⁻¹ = 7.6256740434(70) × 10⁻⁸) [ħ⁻²𝘤⁴mₑ³ϕ⁻²g₀⁻³] 統一

Solar radiation unit (kg⋅s⁻² or lb⋅ft⁻¹).

```

Julia julia> langley(Metric) # kg⋅s⁻² Ωᵢₜ⁻¹Vᵢₜ²2⁶3²5⁵43⁻¹ = 41867.37323211056 [N⋅m⁻¹] メトリック

julia> langley(CGS) # g⋅s⁻² Ωᵢₜ⁻¹Vᵢₜ²2⁹3²5⁸43⁻¹ = 4.186737323211056×10⁷ [dyn⋅cm⁻¹] ガウス

julia> langley(English) # lb⋅ft⁻¹ g₀⁻¹ft⋅lb⁻¹Ωᵢₜ⁻¹Vᵢₜ²2⁶3²5⁵43⁻¹ = 2868.8263456495906 [lbf⋅ft⁻¹] 英語 ```
