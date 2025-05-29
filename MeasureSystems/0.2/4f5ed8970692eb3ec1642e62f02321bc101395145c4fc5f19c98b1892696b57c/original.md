```Julia
gilbert(U::UnitSystem) = abampere(U)/𝟐/turn(U)
nonstandard : [T⁻¹QA⁻¹], [T⁻¹Q], [T⁻¹Q], [M¹ᐟ²L¹ᐟ²T⁻¹], [M¹ᐟ²L³ᐟ²T⁻²]
T⁻¹QA⁻¹⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²R∞⁻¹α²τ⁻¹2⁻⁴5⁻⁵ᐟ² = 0.00193737235568(59)) [ħ⁻¹ᐟ²𝘤³ᐟ²μ₀⁻¹ᐟ²mₑ⋅ϕ⁻³ᐟ²λ⁻¹ᐟ²αL⁻¹g₀⁻¹] Unified
```

Electromagnetic unit of magnetization (Gb).

```Julia
julia> gilbert(Metric) # A⋅rad⁻¹
τ⁻¹5 = 0.7957747154594768 [s⁻¹C] Metric

julia> gilbert(EMU) # Gb
τ⁻¹2⁻¹ = 0.07957747154594767 [Mx⋅cm⁻¹] EMU

julia> gilbert(ESU) # statA⋅rad⁻¹
𝘤⋅τ⁻¹2⋅5² = 2.385672579618471×10⁹ [g¹ᐟ²cm³ᐟ²s⁻²] ESU
```
