```Julia
abohm(U::UnitSystem) = resistance(𝟏,U,EMU)
resistance : [FLTQ⁻²], [FLTQ⁻²], [ML²T⁻¹Q⁻²], [LT⁻¹], [L⁻¹T]
FLTQ⁻²⋅(𝘃⁻¹τ⁻¹2⁻³5⁻² = 2.654418729438073×10⁻¹²) [𝘃⋅μ₀⋅λ⋅αL²] 統一

電磁単位の `resistance` (Ω)。

```

Julia julia> abohm(Metric) # Ω 2⁻⁹5⁻⁹ = 1.0×10⁻⁹ [Ω] Metric

julia> abohm(EMU) # abΩ 𝟏 = 1.0 [cm⋅s⁻¹] EMU

julia> abohm(ESU) # statΩ 𝘃⁻²2⁻⁴5⁻⁴ = 1.1126500560536184×10⁻²¹ [cm⁻¹s] ESU ```
