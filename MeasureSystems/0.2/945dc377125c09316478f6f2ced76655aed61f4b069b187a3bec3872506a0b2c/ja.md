```Julia
jansky(U::UnitSystem) = fluence(𝟏𝟎^-26,U,Metric)
fluence : [FL⁻¹], [FL⁻¹], [MT⁻²], [MT⁻²], [MT⁻²]
FL⁻¹⋅(𝘩⁻¹𝘤⁻¹R∞⁻³α⁶τ⁻²2⁻²⁹5⁻²⁶ = 1.8213882206(17) × 10⁻³⁸) [ħ⁻²𝘤⁴mₑ³ϕ⁻²g₀⁻³] 統一

スペクトル放射照度の基準単位 (kg⋅s⁻² または lb⋅ft⁻¹)。

```

Julia julia> jansky(Metric) # kg⋅s⁻² 2⁻²⁶5⁻²⁶ = 1.0×10⁻²⁶ [N⋅m⁻¹] メトリック

julia> jansky(CGS) # g⋅s⁻² 2⁻²³5⁻²³ = 1.0×10⁻²³ [dyn⋅cm⁻¹] ガウス

julia> jansky(English) # lb⋅ft⁻¹ g₀⁻¹ft⋅lb⁻¹2⁻²⁶5⁻²⁶ = 6.852176585679177×10⁻²⁸ [lbf⋅ft⁻¹] 英語 ```
