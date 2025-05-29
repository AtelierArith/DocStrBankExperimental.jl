```Julia
weber(U::UnitSystem) = magneticflux(𝟏,U,Metric)
magneticflux : [FLTQ⁻¹C], [FLTQ⁻¹], [ML²T⁻¹Q⁻¹], [M¹ᐟ²L³ᐟ²T⁻¹], [M¹ᐟ²L¹ᐟ²]
FLTQ⁻¹C⋅(𝘩⁻¹ᐟ²𝘃⁻¹ᐟ²2³5⁷ᐟ² = 5.017029284119592×10¹⁵) [ħ¹ᐟ²𝘃¹ᐟ²μ₀¹ᐟ²ϕ¹ᐟ²λ¹ᐟ²] 統一

Metric unit of `magneticflux` (Wb).

```

Julia julia> weber(Metric) # Wb 𝟏 = 1.0 [Wb] メトリック

julia> weber(EMU) # Mx 2⁸5⁸ = 1.0×10⁸ [Mx] EMU

julia> weber(ESU) # statWb 𝘃⁻¹2⁶5⁶ = 0.0033356409519815205 [g¹ᐟ²cm¹ᐟ²] ESU ```
