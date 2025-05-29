```Julia
ampere(U::UnitSystem) = current(𝟏,U,Metric)
current : [T⁻¹Q], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
T⁻¹Q⋅(𝘩⁻¹ᐟ²𝘃⁻¹ᐟ²R∞⁻¹α²2⁻⁴5⁻⁷ᐟ² = 0.00243457390395(75)) [ħ⁻¹ᐟ²𝘃³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] 統一

Metric unit of `current` (C⋅s⁻¹).

```

Julia julia> ampere(Metric) # C⋅s⁻¹ 𝟏 = 1.0 [s⁻¹C] Metric

julia> ampere(EMU) # abC⋅s⁻¹ 2⁻¹5⁻¹ = 0.1 [Mx⋅cm⁻¹] EMU

julia> ampere(ESU) # statC⋅s⁻¹ 𝘤⋅2⋅5 = 2.99792458×10⁹ [g¹ᐟ²cm³ᐟ²s⁻²] ESU ```
