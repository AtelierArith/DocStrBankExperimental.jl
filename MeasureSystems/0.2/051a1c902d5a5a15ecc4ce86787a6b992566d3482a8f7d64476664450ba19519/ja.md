```Julia
gauss(U::UnitSystem) = magneticfluxdensity(𝟏,U,EMU)
magneticfluxdensity : [FL⁻¹TQ⁻¹C], [FL⁻¹TQ⁻¹], [MT⁻¹Q⁻¹], [M¹ᐟ²L⁻¹ᐟ²T⁻¹], [M¹ᐟ²L⁻³ᐟ²]
FL⁻¹TQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²R∞⁻²α⁴τ⁻²2⁻³5⁻¹ᐟ² = 7.4813429063(46) × 10⁻¹⁴) [ħ⁻³ᐟ²𝘤⁵ᐟ²μ₀¹ᐟ²mₑ²ϕ⁻³ᐟ²λ¹ᐟ²g₀⁻²] 統一

```

`magneticfluxdensity` の電磁単位 (T)。

```Julia
julia> gauss(Metric) # T
2⁻⁴5⁻⁴ = 0.0001 [T] メトリック

julia> gauss(EMU) # G
𝟏 = 1.0 [G] EMU

julia> gauss(ESU) # statT
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g¹ᐟ²cm⁻³ᐟ²] ESU
```
