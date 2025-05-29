```Julia
abcoulomb(U::UnitSystem) = charge(𝟏,U,EMU)
charge : [Q], [Q], [Q], [M¹ᐟ²L¹ᐟ²], [M¹ᐟ²L³ᐟ²T⁻¹]
Q⋅(𝘩⁻¹ᐟ²𝘃¹ᐟ²τ⋅2⁻²5⁻⁵ᐟ² = 1.8900670148532572×10¹⁹) [ħ¹ᐟ²𝘃⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

電磁単位の `charge` (C)。

```

Julia julia> abcoulomb(Metric) # C 2⋅5 = 10.0 [C] メトリック

julia> abcoulomb(EMU) # abC 𝟏 = 1.0 [g¹ᐟ²cm¹ᐟ²] EMU

julia> abcoulomb(ESU) # statC 𝘃⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻¹] ESU ```
