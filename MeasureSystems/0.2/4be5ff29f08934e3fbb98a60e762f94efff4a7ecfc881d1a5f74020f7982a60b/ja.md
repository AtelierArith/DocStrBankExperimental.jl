```Julia
lightyear(U::UnitSystem) = year(U)*lightspeed(U)
length : [L], [L], [L], [L], [L]
L⋅(𝘤⋅R∞⋅α⁻²aⱼ⋅τ⋅2⁸3³5² = 2.44995556434(75) × 10²⁸) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

Unit of `length` defined by distance traveled by light in 1 `year` unit.

```

Julia julia> lightyear(Metric) # m 𝘤⋅aⱼ⋅2⁷3³5² = 9.4607304725808×10¹⁵ [m] メトリック

julia> lightyear(English) # ft 𝘤⋅aⱼ⋅ft⁻¹2⁷3³5² = 3.103914197040945×10¹⁶ [ft] 英語

julia> lightyear(IAU) # au 𝘤⋅aⱼ⋅au⁻¹2⁷3³5² = 63241.0770843(13) [au] IAU☉ ```
