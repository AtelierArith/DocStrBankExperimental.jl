```Julia
current : [T⁻¹Q], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
current(U::UnitSystem,S::UnitSystem) = charge(U,S)/time(U,S)
current(v::Real,U::UnitSystem,S::UnitSystem) = v/current(U,S)
T⁻¹Q [ħ⁻¹ᐟ²𝘤³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] 統一

電気の `charge` の流れは `time` または `current` (A, C⋅s⁻¹) で、単位変換係数。

```

Julia julia> current(EMU,Metric) # A⋅Bi⁻¹ 2⋅5 = 10.0 [C]/[g¹ᐟ²cm¹ᐟ²] EMU -> Metric

julia> current(EMU,ESU) # statA⋅Bi⁻¹ 𝘃⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻¹]/[g¹ᐟ²cm¹ᐟ²] EMU -> ESU

julia> current(ESU,Metric) # A⋅statA⁻¹ 𝘃⁻¹2⁻¹5⁻¹ = 3.3356409519815207×10⁻¹⁰ [C]/[g¹ᐟ²cm³ᐟ²s⁻¹] ESU -> Metric

julia> current(Metric,SI2019) # A⋅A⁻¹ 𝘩⁻¹ᐟ²𝘤¹ᐟ²𝘦⋅α⁻¹ᐟ²τ¹ᐟ²2⁻⁷ᐟ²5⁻⁷ᐟ² = 0.999999999727(77) [C]/[C] Metric -> SI2019 ```
