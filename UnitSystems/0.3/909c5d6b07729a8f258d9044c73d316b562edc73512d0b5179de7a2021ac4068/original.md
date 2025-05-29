```Julia
illuminance(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/area(U,S)
illuminance(v::Real,U::UnitSystem,S::UnitSystem) = v/illuminance(U,S)
```

Luminous flux per `area` or `luminance` (lx, lm⋅m⁻², cd⋅m⁻²⋅rad²), unit conversion factor.

```Julia
julia> illuminance(CGS,Metric) # lx⋅ph⁻¹
9999.999999999996

julia> illuminance(IAU,Metric) # lx⋅au²⋅lm⁻¹
4.4683704995197134e-23

julia> illuminance(English,Metric) # ft²⋅m⁻²
10.763910416709722

julia> 1/10.76 # lx⋅fc⁻¹
0.0929368029739777
```
