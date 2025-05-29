```Julia
statampere(U::UnitSystem) = current(𝟏,U,ESU)
current : [T⁻¹Q], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
T⁻¹Q⋅(𝘩⁻¹ᐟ²𝘤⁻³ᐟ²R∞⁻¹α²2⁻⁵5⁻⁹ᐟ² = 8.1208644146(25) × 10⁻¹³) [ħ⁻¹ᐟ²𝘤³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] 統一

静電単位の `current` (C⋅s⁻¹)。

```

Julia julia> statampere(Metric) # C⋅s⁻¹ 𝘃⁻¹2⁻¹5⁻¹ = 3.3356409519815207×10⁻¹⁰ [s⁻¹C] メトリック

julia> statampere(EMU) # abC⋅s⁻¹ 𝘃⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [Mx⋅cm⁻¹] EMU

julia> statampere(ESU) # statC⋅s⁻¹ 𝟏 = 1.0 [g¹ᐟ²cm³ᐟ²s⁻²] ESU ```
