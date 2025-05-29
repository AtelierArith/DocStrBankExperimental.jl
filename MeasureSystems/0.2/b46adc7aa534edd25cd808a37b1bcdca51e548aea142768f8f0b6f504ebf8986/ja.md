```Julia
elementarycharge(U::UnitSystem) = √(𝟐*planck(U)*finestructure(U)/vacuumimpedance(U))
charge : [Q], [Q], [Q], [M¹ᐟ²L¹ᐟ²], [M¹ᐟ²L³ᐟ²T⁻¹]
Q⋅(α¹ᐟ²τ¹ᐟ²2¹ᐟ² = 0.302822120872(23)) [ħ¹ᐟ²𝘤⁻¹ᐟ²μ₀⁻¹ᐟ²ϕ¹ᐟ²λ⁻¹ᐟ²αL⁻¹] 統一

量子化された素電荷 `𝘦` のプロトンまたは電子 `2/(klitzing(U)*josephson(U))` (C)。

```

Julia julia> elementarycharge(SI2019) # C 𝘦 = 1.602176634×10⁻¹⁹ [C] SI2019

julia> elementarycharge(Metric) # C 𝘩¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.60217663444(12) × 10⁻¹⁹ [C] Metric

julia> elementarycharge(CODATA) # C RK⁻¹KJ⁻¹2 = 1.6021766207(99) × 10⁻¹⁹ [C] CODATA

julia> elementarycharge(Conventional) # C RK90⁻¹KJ90⁻¹2 = 1.602176491612271×10⁻¹⁹ [C] Conventional

julia> elementarycharge(International) # C 𝘩¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²Ωᵢₜ⋅Vᵢₜ⁻¹τ⁻¹ᐟ²2⁷ᐟ²5⁷ᐟ² = 1.60244090637(12) × 10⁻¹⁹ [C] International

julia> elementarycharge(EMU) # abC 𝘩¹ᐟ²𝘤⁻¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁵ᐟ²5⁵ᐟ² = 1.60217663444(12) × 10⁻²⁰ [g¹ᐟ²cm¹ᐟ²] EMU

julia> elementarycharge(ESU) # statC 𝘩¹ᐟ²𝘤¹ᐟ²α¹ᐟ²τ⁻¹ᐟ²2⁹ᐟ²5⁹ᐟ² = 4.80320471388(37) × 10⁻¹⁰ [g¹ᐟ²cm³ᐟ²s⁻¹] ESU

julia> elementarycharge(Hartree) # 𝘦 𝟏 = 1.0 [𝘦] Hartree ```
