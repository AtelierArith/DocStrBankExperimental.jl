```Julia
abampere(U::UnitSystem) = current(𝟏,U,EMU)
current : [T⁻¹Q], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
T⁻¹Q⋅(𝘩⁻¹ᐟ²𝘃⁻¹ᐟ²R∞⁻¹α²2⁻³5⁻⁵ᐟ² = 0.0243457390395(75)) [ħ⁻¹ᐟ²𝘃³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] 統一

電磁単位の `current` (C⋅s⁻¹)。

```

Julia julia> abampere(Metric) # C⋅s⁻¹ 2⋅5 = 10.0 [s⁻¹C] Metric

julia> abampere(EMU) # abC⋅s⁻¹ 𝟏 = 1.0 [Mx⋅cm⁻¹] EMU

julia> abampere(ESU) # statC⋅s⁻¹ 𝘃⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻²] ESU ```
