```Julia
lunardistance(U::UnitSystem) = length(𝟏,U,IAUE)
length : [L], [L], [L], [L], [L]
L⋅14237 [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

地球と月の標準距離 (m または ft)。

```

Julia julia> lunardistance(Metric) # m 2³3³5³⋅14237 = 3.84399×10⁸ [m] メトリック

julia> lunardistance(Nautical) # nm g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁸3⁶5⁵⋅14237 = 207275.31409(21) [nm] 海里

julia> lunardistance(Metric)/lightspeed(Metric) # s 𝘤⁻¹2³3³5³⋅14237 = 1.2822170463007445 [s] メトリック ```
