```Julia
molargas(U::UnitSystem) = boltzmann(x)*avogadro(x)
molarentropy : [FLΘ⁻¹N⁻¹], [FLΘ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹], [ML²T⁻²Θ⁻¹N⁻¹]
FLΘ⁻¹N⁻¹⋅(μₑᵤ = 0.000548579909065(16)) [kB⋅mₑ⁻¹Mᵤ] Unified
```

Universal gas constant `Rᵤ` is factored into specific `gasconstant(x)*molarmass(x)` values.

```Julia
julia> molargas(SI2019) # J⋅K⁻¹⋅mol⁻¹
kB⋅NA = 8.31446261815324 [J⋅K⁻¹mol⁻¹] SI2019

julia> molargas(English)/𝟐^4/𝟑^2 # psi⋅ft³⋅°R⁻¹⋅lb-mol⁻¹
kB⋅NA⋅g₀⁻¹ft⁻¹2⁻¹3⁻⁴5⁴ = 10.731577089016287 [lbf⋅ft⋅°R⁻¹lb-mol⁻¹] English

julia> molargas(English)/atmosphere(English) # atm⋅ft³⋅R⁻¹⋅lb-mol⁻¹
kB⋅NA⋅ft⁻³lb⋅atm⁻¹2³3⁻²5⁴ = 0.7302405072952731 [ft³°R⁻¹lb-mol⁻¹] English

julia> molargas(English)/thermalunit(English) # BTU⋅°R⁻¹⋅lb-mol⁻¹
kB⋅NA⋅Ωᵢₜ⋅Vᵢₜ⁻²2⁻²3⁻²5⁻¹43 = 1.9859050081929637 [°R⁻¹lb-mol⁻¹] English

julia> molargas(Metric)/atmosphere(Metric) # atm⋅m³⋅K⁻¹⋅mol⁻¹
kB⋅NA⋅atm⁻¹ = 8.205736608095969×10⁻⁵ [m³K⁻¹mol⁻¹] Metric

julia> molargas(Metric)/torr(Metric) # m³⋅torr⋅K⁻¹⋅mol⁻¹
kB⋅NA⋅atm⁻¹2³5⋅19 = 0.062363598221529364 [m³K⁻¹mol⁻¹] Metric

julia> molargas(English)/torr(English) # ft³⋅torr⋅°R⁻¹⋅lb-mol⁻¹
kB⋅NA⋅ft⁻³lb⋅atm⁻¹2⁶3⁻²5⁵19 = 554.9827855444075 [ft³°R⁻¹lb-mol⁻¹] English

julia> molargas(CGS) # erg⋅K⁻¹⋅mol⁻¹
kB⋅NA⋅2⁷5⁷ = 8.31446261815324×10⁷ [erg⋅K⁻¹mol⁻¹] Gauss

julia> molargas(English) # ft⋅lb⋅°R⁻¹⋅lb-mol⁻¹
kB⋅NA⋅g₀⁻¹ft⁻¹2³3⁻²5⁴ = 1545.3471008183453 [lbf⋅ft⋅°R⁻¹lb-mol⁻¹] English

julia> molargas(British) # ft⋅lb⋅°R⁻¹⋅slug-mol⁻¹
kB⋅NA⋅ft⁻²2³3⁻²5⁴ = 49720.07265826846 [lb⋅ft⋅°R⁻¹slug-mol⁻¹] British

julia> molargas(SI1976) # J⋅K⁻¹⋅mol⁻¹ (US1976 Standard Atmosphere)
8.31432 = 8.31432 [kg⋅m²s⁻²K⁻¹mol⁻¹] SI1976
```
