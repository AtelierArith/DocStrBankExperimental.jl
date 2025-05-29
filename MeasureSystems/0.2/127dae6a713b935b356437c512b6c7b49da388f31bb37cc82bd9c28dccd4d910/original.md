```Julia
maxwell(U::UnitSystem) = magneticflux(𝟏,U,EMU)
magneticflux : [FLTQ⁻¹C], [FLTQ⁻¹], [ML²T⁻¹Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²]
FLTQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘤⁻¹ᐟ²2⁻⁵5⁻⁹ᐟ² = 5.017029284119592×10⁷) [ħ¹ᐟ²𝘤¹ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²] Unified
```

Electromagnetic unit of `magneticflux` (Wb).

```Julia
julia> maxwell(Metric) # Wb
2⁻⁸5⁻⁸ = 1.0×10⁻⁸ [Wb] Metric

julia> maxwell(EMU) # Mx
𝟏 = 1.0 [Mx] EMU

julia> maxwell(ESU) # statWb
𝘤⁻¹2⁻²5⁻² = 3.335640951981521×10⁻¹¹ [g¹ᐟ²cm¹ᐟ²] ESU
```
