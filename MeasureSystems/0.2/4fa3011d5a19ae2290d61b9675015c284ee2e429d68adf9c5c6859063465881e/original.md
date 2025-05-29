```Julia
photonradiance : [L⁻²TA⁻²], [L⁻²T], [L⁻²T], [L⁻²T], [L⁻²T]
photonradiance(U::UnitSystem,S::UnitSystem) = photonirradiance(U,S)/solidangle(U,S)
photonradiance(v::Real,U::UnitSystem,S::UnitSystem) = v/photonradiance(U,S)
L⁻²TA⁻² [ħ⁻¹mₑ⋅ϕ⁻³g₀⁻¹] Unified
```

Photon radiance or `photonirradiance` per `solidangle` (Hz⋅m⁻², m⁻²⋅s⁻¹), unit conversion factor.

```Julia
julia> photonradiance(CGS,Metric) # cm²⋅m⁻²
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] Gauss -> Metric

julia> photonradiance(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] English -> Metric
```
