```Julia
mile(U::UnitSystem) = length(𝟏,U,MPH)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2⁶3⋅5⋅11 = 4.1675653896(13) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

法定 `English` マイル (m または ft)。

```

Julia julia> mile(Metric) # m ft⋅2⁵3⋅5⋅11 = 1609.344 [m] メトリック

julia> mile(English) # ft 2⁵3⋅5⋅11 = 5280.0 [ft] 英語

julia> mile(Nautical) # nm ft⋅ftUS⁻¹2⁵3⋅5⋅11 = 5279.989440000001 [ft] 調査 ```
