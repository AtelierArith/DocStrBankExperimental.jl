```Julia
meter(U::UnitSystem) = length(𝟏,U,Metric)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²τ⋅2 = 2.58960507484(79) × 10¹²) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

Metric unit of `length` (m or ft).

```

Julia julia> meter(CGS) # cm 2²5² = 100.0 [cm] ガウス

julia> meter(English) # ft ft⁻¹ = 3.280839895013123 [ft] 英語

julia> meter(Meridian) # em g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹5⁷ = 0.9985540395(10) [em] メリディアン ```
