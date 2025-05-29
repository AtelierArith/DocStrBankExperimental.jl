```Julia
illuminance : [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
illuminance(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/area(U,S)
illuminance(v::Real,U::UnitSystem,S::UnitSystem) = v/illuminance(U,S)
L⁻²J [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻³g₀⁻⁴] Unified
```

Luminous flux per `area` or `luminance` (lx, lm⋅m⁻², cd⋅m⁻²⋅rad²), unit conversion factor.

```Julia
julia> illuminance(CGS,Metric) # lx⋅ph⁻¹
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] Gauss -> Metric

julia> illuminance(IAU,Metric) # lx⋅au²⋅lm⁻¹
au⁻² = 4.46837049952(18) × 10⁻²³ [m⁻²]/[au⁻²] IAU☉ -> Metric

julia> illuminance(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] English -> Metric

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
