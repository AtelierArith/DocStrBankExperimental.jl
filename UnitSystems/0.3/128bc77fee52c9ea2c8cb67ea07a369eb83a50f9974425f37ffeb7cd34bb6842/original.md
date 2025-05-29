```Julia
luminance(U::UnitSystem,S::UnitSystem) = luminousintensity(U,S)/area(U,S)
luminance(v::Real,U::UnitSystem,S::UnitSystem) = v/luminance(U,S)
```

Luminous intensity per `area` or `luminance` (cd⋅m⁻², lm⋅m⁻²⋅rad⁻²), unit conversion factor.

```Julia
julia> luminance(CGS,Metric) # lx⋅ph⁻¹
9999.999999999996

julia> luminance(IAU,Metric) # lx⋅au²⋅lm⁻¹
4.4683704995197134e-23

julia> luminance(English,Metric) # ft²⋅m⁻²
10.763910416709722

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
