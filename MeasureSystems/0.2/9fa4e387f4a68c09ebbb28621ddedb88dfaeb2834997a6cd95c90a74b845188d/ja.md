```Julia
technicalatmosphere(U::UnitSystem) = kilopond(U)/(centi*meter(U))^2
圧力 : [FL⁻²], [FL⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²], [ML⁻¹T⁻²]
FL⁻²⋅(𝘩⁻¹𝘤⁻¹R∞⁻⁴α⁸g₀⋅τ⁻³5⁴ = 6.8974674816(85) × 10⁻²⁰) [ħ⁻³𝘤⁵mₑ⁴ϕ⁻³g₀⁻⁴] 統一

重力単位の `圧力` (Pa または lb⋅ft⁻²)。

```

Julia julia> technicalatmosphere(Metric) # Pa g₀⋅2⁴5⁴ = 98066.5 [Pa] メトリック

julia> technicalatmosphere(English) # lb⋅ft⁻² ft²lb⁻¹2⁴5⁴ = 2048.161436225217 [lbf⋅ft⁻²] 英語

julia> technicalatmosphere(IPS) # lb⋅in⁻² ft²lb⁻¹3⁻²5⁴ = 14.223343307119563 [lb⋅in⁻²] IPS ```
