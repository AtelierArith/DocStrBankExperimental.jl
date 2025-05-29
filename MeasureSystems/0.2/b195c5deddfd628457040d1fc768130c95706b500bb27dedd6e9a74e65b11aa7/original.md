```Julia
soundexposure : [F²L⁻⁴T], [F²L⁻⁴T], [M²L⁻²T⁻³], [M²L⁻²T⁻³], [M²L⁻²T⁻³]
soundexposure(U::UnitSystem,S::UnitSystem) = pressure(U,S)^2*time(U,S)
soundexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/soundexposure(U,S)
F²L⁻⁴T [ħ⁻⁵𝘤⁸mₑ⁷ϕ⁻⁵g₀⁻⁷] Unified
```

Square of `pressure` by `time` or `soundexposure` (Pa²⋅s, N²⋅m⁻⁴), unit conversion factor.

```Julia
julia> soundexposure(CGS,Metric) # Pa²⋅Ba⁻²
2⁻²5⁻² = 0.010000000000000002 [kg²m⁻²s⁻⁴]/[g²cm⁻²s⁻⁴] Gauss -> Metric

julia> soundexposure(English,Metric) # Pa²⋅ft⁴⋅lb⁻²
g₀²ft⁻⁴lb² = 2292.519200024031 [kg²m⁻²s⁻⁴]/[lbf²ft⁻⁴] English -> Metric
```
