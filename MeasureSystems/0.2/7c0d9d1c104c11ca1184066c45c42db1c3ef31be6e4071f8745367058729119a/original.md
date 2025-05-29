```Julia
rayleigh(U::UnitSystem) = photonirradiance(𝟏𝟎^10,U,Metric)
photonirradiance : [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T]
L⁻²T⋅(𝘤⋅R∞⁻¹α²τ⁻¹2⁹5¹⁰ = 1.15767636121(35) × 10⁶) [ħ⁻¹mₑ⋅ϕ⁻¹g₀⁻¹] Unified
```

Common unit of `photonirradiance` (Hz⋅m⁻²).

```Julia
julia> rayleigh(Metric) # Hz⋅m⁻²
2¹⁰5¹⁰ = 1.0×10¹⁰ [Hz⋅m⁻²] Metric

julia> rayleigh(CGS) # Hz⋅cm⁻²
2⁶5⁶ = 1.0×10⁶ [Hz⋅m⁻²] Gauss

julia> rayleigh(English) # Hz⋅ft⁻²
ft²2¹⁰5¹⁰ = 9.290304000000001×10⁸ [ft⁻²s] English
```
