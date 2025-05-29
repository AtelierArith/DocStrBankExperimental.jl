```Julia
statvolt(U::UnitSystem) = electricpotential(𝟏,U,ESU)
electricpotential : [FLQ⁻¹], [FLQ⁻¹], [ML²T⁻²Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻²], [M¹ᐟ²L¹ᐟ²T⁻¹]
FLQ⁻¹⋅(𝘩⁻¹ᐟ²𝘃⁻¹ᐟ²R∞⁻¹α²τ⁻¹2⁻⁴5⁻⁵ᐟ² = 0.00193737235568(59)) [ħ⁻¹ᐟ²𝘃⁵ᐟ²μ₀¹ᐟ²mₑ⋅ϕ⁻¹ᐟ²λ¹ᐟ²αL⋅g₀⁻¹] 統一

静電単位の `electricpotential` (V)。

```

Julia julia> statvolt(Metric) # V 𝘃⋅2⁻⁶5⁻⁶ = 299.792458 [V] メトリック

julia> statvolt(EMU) # abV 𝘃⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm³ᐟ²s⁻²] EMU

julia> statvolt(ESU) # statV 𝟏 = 1.0 [g¹ᐟ²cm¹ᐟ²s⁻¹] ESU ```
