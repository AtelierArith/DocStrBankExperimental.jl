```Julia
oersted(U::UnitSystem) = magneticfield(𝟏,U,EMU)
magneticfield : [L⁻¹T⁻¹QRC⁻¹], [L⁻¹T⁻¹Q], [L⁻¹T⁻¹Q], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²T⁻²]
L⁻¹T⁻¹QRC⁻¹⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²R∞⁻²α⁴τ⁻²2⁻³5⁻¹ᐟ² = 7.4813429063(46) × 10⁻¹⁴) [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀⁻¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] 統一

```

電磁単位の `magneticfield` (Oe)。

```Julia
julia> oersted(Metric) # A⋅m⁻¹
τ⁻¹2²5³ = 79.57747154594767 [m⁻¹s⁻¹C] メトリック

julia> oersted(EMU) # Oe
𝟏 = 1.0 [G] EMU

julia> oersted(ESU) # statA⋅cm⁻¹
𝘤⋅2²5² = 2.99792458×10¹⁰ [g¹ᐟ²cm¹ᐟ²s⁻²] ESU
```
