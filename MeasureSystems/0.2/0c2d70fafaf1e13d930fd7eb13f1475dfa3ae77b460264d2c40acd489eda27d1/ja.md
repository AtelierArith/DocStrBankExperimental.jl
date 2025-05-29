```Julia
meridianmile(U::UnitSystem) = length(𝟐^4*𝟓^5/𝟑^3,U,Metric)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²τ⋅2⁵3⁻³5⁵ = 4.7955649534(15) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

古典的海里は単純な子午線の仮定によって定義される（mまたはft）。

```

Julia julia> meridianmile(Metric) # m 2⁴3⁻³5⁵ = 1851.8518518518517 [m] メトリック

julia> meridianmile(English) # ft ft⁻¹2⁴3⁻³5⁵ = 6075.6294352094865 [ft] 英語

julia> meridianmile(Nautical) # nm g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹5⁷ = 0.9985540395(10) [nm] 海里 ```
