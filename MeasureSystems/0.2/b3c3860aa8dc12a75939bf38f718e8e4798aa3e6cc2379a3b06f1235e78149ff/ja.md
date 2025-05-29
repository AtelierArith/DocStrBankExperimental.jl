```Julia
parsec(U::UnitSystem) = astronomicalunit(U)*𝟐^2*𝟑^4*𝟓^3/τ
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²au⋅2⁸3⁴5³ = 7.9906863243(25) × 10²⁸) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

Unit of `length` defined at which 1 `astronomicalunit` subtends an angle of 1 arcsecond.

```

Julia julia> parsec(Metric) # m au⋅τ⁻¹2⁷3⁴5³ = 3.085677581491(62) × 10¹⁶ [m] メトリック

julia> parsec(English) # ft au⋅ft⁻¹τ⁻¹2⁷3⁴5³ = 1.012361411250(20) × 10¹⁷ [ft] 英語

julia> parsec(IAU) # au τ⁻¹2⁷3⁴5³ = 206264.80624709636 [au] IAU☉ ```
