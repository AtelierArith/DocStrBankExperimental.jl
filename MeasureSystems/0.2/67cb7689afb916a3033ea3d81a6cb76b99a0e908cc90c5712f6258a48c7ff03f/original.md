```Julia
luminance : [L⁻²JA⁻²], [L⁻²J], [L⁻²J], [L⁻²J], [L⁻²J]
luminance(U::UnitSystem,S::UnitSystem) = luminousintensity(U,S)/area(U,S)
luminance(v::Real,U::UnitSystem,S::UnitSystem) = v/luminance(U,S)
L⁻²JA⁻² [ħ⁻³𝘤⁶mₑ⁴Kcd⋅ϕ⁻⁵g₀⁻⁴] Unified
```

Luminous intensity per `area` or `luminance` (cd⋅m⁻², lm⋅m⁻²⋅rad⁻²), unit conversion factor.

```Julia
julia> luminance(CGS,Metric) # lx⋅ph⁻¹
2⁴5⁴ = 10000.0 [m⁻²]/[cm⁻²] Gauss -> Metric

julia> luminance(IAU,Metric) # lx⋅au²⋅lm⁻¹
au⁻² = 4.46837049952(18) × 10⁻²³ [m⁻²]/[au⁻²] IAU☉ -> Metric

julia> luminance(English,Metric) # ft²⋅m⁻²
ft⁻² = 10.76391041670972 [m⁻²]/[ft⁻²] English -> Metric

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
