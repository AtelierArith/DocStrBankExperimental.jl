```Julia
earthmeter(U::UnitSystem) = greatcircle(U)/𝟐^9/𝟓^7
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²g₀⁻¹ᐟ²GME¹ᐟ²τ²2⁻⁸5⁻⁷ = 2.5933549636(27) × 10¹²) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

メルカトル単位の `length` は、フランスで元々定義された通り (m または ft)。

```

Julia julia> earthmeter(CGS) # cm g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻⁷5⁻⁵ = 100.144805430(10) [cm] ガウス

julia> earthmeter(English) # ft g₀⁻¹ᐟ²ft⁻¹GME¹ᐟ²τ⋅2⁻⁹5⁻⁷ = 3.2855907293(33) [ft] 英語

julia> earthmeter(Meridian) # em 𝟏 = 1.0 [em] メルカトル ```
