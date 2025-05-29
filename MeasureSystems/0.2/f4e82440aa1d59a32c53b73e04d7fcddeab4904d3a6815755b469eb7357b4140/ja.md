```Julia
nauticalmile(U::UnitSystem) = greatcircle(U)/𝟐^5/𝟑^3/𝟓^2
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²g₀⁻¹ᐟ²GME¹ᐟ²τ²2⁻⁴3⁻³5⁻² = 4.8025091919(50) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] 統一

標準の `nauticalmile` は `earthradius` によって定義されます (m または ft)。

```

Julia julia> nauticalmile(Metric) # m g₀⁻¹ᐟ²GME¹ᐟ²τ⋅2⁻⁵3⁻³5⁻² = 1854.5334339(19) [m] メトリック

julia> nauticalmile(Meridian) # em 2⁴3⁻³5⁵ = 1851.8518518518517 [em] メリディアン

julia> nauticalmile(English) # ft g₀⁻¹ᐟ²ft⁻¹GME¹ᐟ²τ⋅2⁻⁵3⁻³5⁻² = 6084.4272766(61) [ft] 英語 ```
