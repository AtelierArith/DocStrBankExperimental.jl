```Julia
barn(U::UnitSystem) = area((𝟐*𝟓)^-28,U,Metric)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴τ²2⁻²⁶5⁻²⁸ = 0.00067060544436(41)) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] 統一

面積の単位は `100` 平方フェムトメートル (m² または ft²) で定義されています。

```

Julia julia> barn(Metric) # m² 2⁻²⁸5⁻²⁸ = 1.0×10⁻²⁸ [m²] メトリック

julia> barn(CGS) # cm² 2⁻²⁴5⁻²⁴ = 1.0×10⁻²⁴ [cm²] ガウス

julia> barn(English) # ft² ft⁻²2⁻²⁸5⁻²⁸ = 1.076391041670972×10⁻²⁷ [ft²] 英語 ```
