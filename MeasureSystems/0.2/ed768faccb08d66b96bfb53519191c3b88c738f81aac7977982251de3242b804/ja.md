```Julia
astronomicalunit(U::UnitSystem) = length(𝟏,U,IAU)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²au⋅τ⋅2 = 3.8739940515(12) × 10²³) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

国際天文学連合からの標準天文単位 (m または ft)。

```

Julia julia> astronomicalunit(Metric) # m au = 1.495978707000(30) × 10¹¹ [m] メトリック

julia> astronomicalunit(English) # ft au⋅ft⁻¹ = 4.908066624016(98) × 10¹¹ [ft] 英語

julia> astronomicalunit(Metric)/lightspeed(Metric) # s 𝘤⁻¹au = 499.004783836(10) [s] メトリック ```
