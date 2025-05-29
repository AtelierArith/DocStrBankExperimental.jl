```Julia
foot(U::UnitSystem) = length(𝟏,U,日本語)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2 = 7.8931162681(24) × 10¹¹) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

日本語単位の `length` (m または ft)。

```

Julia julia> foot(Metric) # m ft = 0.3048 [m] メトリック

julia> foot(Survey) # ftUS ft⋅ftUS⁻¹ = 0.9999980000000002 [ft] サーベイ

julia> foot(IPS) # in 2²3 = 12.0 [in] IPS ```
