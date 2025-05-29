```Julia
lapserate : [L⁻¹Θ], [L⁻¹Θ], [L⁻¹Θ], [L⁻¹Θ], [L⁻¹Θ]
lapserate(U::UnitSystem,S::UnitSystem) = temperature(U,S)/length(U,S)
lapserate(v::Real,U::UnitSystem,S::UnitSystem) = v/lapserate(U,S)
L⁻¹Θ [kB⁻¹ħ⁻¹𝘤³mₑ²ϕ⁻¹g₀⁻²] Unified
```

Temperature gradient over `length` or `lapserate` (K⋅m⁻¹), unit conversion factor.

```Julia
julia> lapserate(Metric,SI2019) # K⋅K⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³ = 0.99999999966(31) [K]/[K] Metric -> SI2019

julia> lapserate(English,SI2019) # K⋅ft⋅°R⁻¹⋅m⁻¹
NA⋅𝘩⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹ft⁻¹2⁴3⁻²5⁴ = 1.82268882994(56) [m⁻¹K]/[ft⁻¹°R] English -> SI2019

julia> lapserate(English,Metric) # K⋅ft⋅°R⁻¹⋅m⁻¹
ft⁻¹3⁻²5 = 1.8226888305628461 [m⁻¹K]/[ft⁻¹°R] English -> Metric

julia> lapserate(EnglishUS,English) # °R⋅ftUS⋅°R⁻¹⋅ft⁻¹
ft⋅ftUS⁻¹ = 0.9999980000000002 [ft⁻¹]/[ft⁻¹] Survey -> English
```
