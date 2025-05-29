```Julia
statweber(U::UnitSystem) = magneticflux(𝟏,U,ESU)
magneticflux : [FLTQ⁻¹C], [FLTQ⁻¹], [ML²T⁻¹Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²]
FLTQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘤¹ᐟ²2⁻³5⁻⁵ᐟ² = 1.5040675409441933×10¹⁸) [ħ¹ᐟ²𝘤¹ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²] Unified
```

Electrostatic unit of `magneticflux` (Wb).

```Julia
julia> statweber(Metric) # Wb
𝘤⋅2⁻⁶5⁻⁶ = 299.792458 [Wb] Metric

julia> statweber(EMU) # Mx
𝘤⋅2²5² = 2.99792458×10¹⁰ [Mx] EMU

julia> statweber(ESU) # statWb
𝟏 = 1.0 [g¹ᐟ²cm¹ᐟ²] ESU
```
