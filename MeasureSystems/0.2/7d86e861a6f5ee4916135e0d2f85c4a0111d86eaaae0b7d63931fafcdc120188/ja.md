```Julia
tesla(U::UnitSystem) = magneticfluxdensity(𝟏,U,Metric)
magneticfluxdensity : [FL⁻¹TQ⁻¹C], [FL⁻¹TQ⁻¹], [MT⁻¹Q⁻¹], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L⁻³ᐟ²]
FL⁻¹TQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²R∞⁻²α⁴τ⁻²2⋅5⁷ᐟ² = 7.4813429063(46) × 10⁻¹⁰) [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] 統一

Metric unit of `magneticfluxdensity` (T).

```

Julia julia> tesla(Metric) # T 𝟏 = 1.0 [T] Metric

julia> tesla(EMU) # G 2⁴5⁴ = 10000.0 [G] EMU

julia> tesla(ESU) # statT 𝘤⁻¹2²5² = 3.3356409519815204×10⁻⁷ [g¹ᐟ²cm⁻³ᐟ²] ESU ```
