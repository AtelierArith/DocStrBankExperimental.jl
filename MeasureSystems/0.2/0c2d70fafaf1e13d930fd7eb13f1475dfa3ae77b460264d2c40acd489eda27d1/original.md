```Julia
meridianmile(U::UnitSystem) = length(𝟐^4*𝟓^5/𝟑^3,U,Metric)
length : [L], [L], [L], [L], [L]
L⋅(R∞⋅α⁻²τ⋅2⁵3⁻³5⁵ = 4.7955649534(15) × 10¹⁵) [ħ⋅𝘤⁻¹mₑ⁻¹ϕ⋅g₀] Unified
```

Historic nautical mile as defined by naive meridian assumption (m or ft).

```Julia
julia> meridianmile(Metric) # m
2⁴3⁻³5⁵ = 1851.8518518518517 [m] Metric

julia> meridianmile(English) # ft
ft⁻¹2⁴3⁻³5⁵ = 6075.6294352094865 [ft] English

julia> meridianmile(Nautical) # nm
g₀¹ᐟ²GME⁻¹ᐟ²τ⁻¹2⁹5⁷ = 0.9985540395(10) [nm] Nautical
```
