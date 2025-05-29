```Julia
hectare(U::UnitSystem) = area(hecto^2,U,Metric)
area : [L²], [L²], [L²], [L²], [L²]
L²⋅(R∞²α⁻⁴τ²2⁶5⁴ = 6.7060544436(41) × 10²⁸) [ħ²𝘤⁻²mₑ⁻²ϕ²g₀²] 統一

土地の面積のメトリック単位は `100` 平方メートル (m² または ft²) で定義されています。

```

Julia julia> hectare(Metric) # m² 2⁴5⁴ = 10000.0 [m²] メトリック

julia> hectare(English) # ft² ft⁻²2⁴5⁴ = 107639.1041670972 [ft²] 英語

julia> hectare(Survey) # ftUS² ftUS⁻²2⁴5⁴ = 107638.67361111114 [ft²] 調査 ```
