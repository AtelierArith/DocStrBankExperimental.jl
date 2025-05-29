```Julia
admiraltymile(U::UnitSystem) = length(𝟐^6*𝟓*𝟏𝟗,U,English)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²ft⋅τ⋅2⁷5⋅19 = 4.7990146910(15) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

クラークの等面半径によって定義された歴史的海里 (m または ft)。

```Julia
julia> admiraltymile(Metric) # m
ft⋅2⁶5⋅19 = 1853.1840000000002 [m] Metric

julia> admiraltymile(English) # ft
2⁶5⋅19 = 6080.0 [ft] English

julia> admiraltymile(Nautical) # nm
g₀¹ᐟ²ft⋅GME⁻¹ᐟ²τ⁻¹2¹¹3³5³19 = 0.9992723594(10) [nm] Nautical
```
