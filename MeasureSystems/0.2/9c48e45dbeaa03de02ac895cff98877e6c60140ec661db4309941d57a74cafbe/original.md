```Julia
wienfrequency(U::UnitSystem) = (𝟑+W₀(-𝟑*exp(-𝟑)))*boltzmann(U)/planck(U)
nonstandard : [T⁻¹Θ⁻¹], [T⁻¹Θ⁻¹], [T⁻¹Θ⁻¹], [T⁻¹Θ⁻¹], [T⁻¹Θ⁻¹]
T⁻¹Θ⁻¹⋅2.8214393721220787 [kB⋅ħ⁻¹ϕ⁻¹] Unified
```

Wien frequency radiation law constant based on Lambert `W₀` evaluation (Hz⋅K⁻¹).

```Julia
julia> wienfrequency(Metric) # Hz⋅K⁻¹
kB⋅NA⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³⋅2.8214393721220787 = 5.8789257556(18) × 10¹⁰ [Hz⋅K⁻¹] Metric

julia> wienfrequency(SI2019) # Hz⋅K⁻¹
kB⋅𝘩⁻¹⋅2.8214393721220787 = 5.8789257576468254×10¹⁰ [Hz⋅K⁻¹] SI2019

julia> wienfrequency(Conventional) # Hz⋅K⁻¹
kB⋅NA⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴5³⋅2.8214393721220787 = 5.8789257556(18) × 10¹⁰ [Hz⋅K⁻¹] Conventional

julia> wienfrequency(CODATA) # Hz⋅K⁻¹
𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹Rᵤ2014⋅2⁴5³⋅2.8214393721220787 = 5.8789238(34) × 10¹⁰ [Hz⋅K⁻¹] CODATA

julia> wienfrequency(English) # Hz⋅°R⁻¹
kB⋅NA⋅𝘤⁻¹R∞⋅α⁻²μₑᵤ⁻¹2⁴3⁻²5⁴⋅2.8214393721220787 = 3.2660698642(10) × 10¹⁰ [Hz⋅°R⁻¹] English
```
