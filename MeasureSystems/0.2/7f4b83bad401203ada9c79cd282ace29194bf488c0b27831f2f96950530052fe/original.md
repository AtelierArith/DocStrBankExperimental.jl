```Julia
stattesla(U::UnitSystem) = magneticfluxdensity(𝟏,U,ESU)
magneticfluxdensity : [FL⁻¹TQ⁻¹C], [FL⁻¹TQ⁻¹], [MT⁻¹Q⁻¹], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L⁻³ᐟ²]
FL⁻¹TQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘤¹ᐟ²R∞⁻²α⁴τ⁻²2⁻¹5³ᐟ² = 0.0022428501790(14)) [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] Unified
```

Electrostatic unit of `magneticfluxdensity` (T).

```Julia
julia> stattesla(Metric) # T
𝘤⋅2⁻²5⁻² = 2.9979245800000005×10⁶ [T] Metric

julia> stattesla(EMU) # G
𝘤⋅2²5² = 2.99792458×10¹⁰ [G] EMU

julia> stattesla(ESU) # statT
𝟏 = 1.0 [g¹ᐟ²cm⁻³ᐟ²] ESU
```
