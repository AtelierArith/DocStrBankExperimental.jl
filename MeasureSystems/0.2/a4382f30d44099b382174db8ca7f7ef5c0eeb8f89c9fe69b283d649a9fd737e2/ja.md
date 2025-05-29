```Julia
statcoulomb(U::UnitSystem) = charge(𝟏,U,ESU)
charge : [Q], [Q], [Q], [M¹ᐟ²L¹ᐟ²], [M¹ᐟ²L³ᐟ²T⁻¹]
Q⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²τ⋅2⁻⁴5⁻⁹ᐟ² = 6.304584936733987×10⁸) [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

静電単位の `charge` (C)。

```

Julia julia> statcoulomb(Metric) # C 𝘃⁻¹2⁻¹5⁻¹ = 3.3356409519815207×10⁻¹⁰ [C] メトリック

julia> statcoulomb(EMU) # abC 𝘃⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g¹ᐟ²cm¹ᐟ²] EMU

julia> statcoulomb(ESU) # statC 𝟏 = 1.0 [g¹ᐟ²cm³ᐟ²s⁻¹] ESU ```
