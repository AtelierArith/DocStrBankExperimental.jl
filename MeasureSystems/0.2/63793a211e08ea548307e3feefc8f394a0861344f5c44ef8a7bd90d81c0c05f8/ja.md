```Julia
coulomb(U::UnitSystem) = charge(𝟏,U,Metric)
charge : [Q], [Q], [Q], [M¹ᐟ²L¹ᐟ²], [M¹ᐟ²L³ᐟ²T⁻¹]
Q⋅(𝘩⁻¹ᐟ²𝘃¹ᐟ²τ⋅2⁻³5⁻⁷ᐟ² = 1.890067014853257×10¹⁸) [ħ¹ᐟ²𝘃⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

Metric unit of `charge` (C).

```

Julia julia> coulomb(Metric) # C 𝟏 = 1.0 [C] Metric

julia> coulomb(EMU) # abC 2⁻¹5⁻¹ = 0.1 [g¹ᐟ²cm¹ᐟ²] EMU

julia> coulomb(ESU) # statC 𝘃⋅2⋅5 = 2.99792458×10⁹ [g¹ᐟ²cm³ᐟ²s⁻¹] ESU ```
