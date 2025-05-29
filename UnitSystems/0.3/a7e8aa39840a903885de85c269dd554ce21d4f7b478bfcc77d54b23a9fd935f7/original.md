```Julia
soundexposure(U::UnitSystem,S::UnitSystem) = pressure(U,S)^2*time(U,S)
soundexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/soundexposure(U,S)
```

Square of `pressure` by `time` or `soundexposure` (Pa²⋅s, N²⋅m⁻⁴), unit conversion factor.

```Julia
julia> soundexposure(CGS,Metric) # Pa²⋅Ba⁻²
0.009999999999999993

julia> soundexposure(English,Metric) # Pa²⋅ft⁴⋅lb⁻²
2292.519200024031
```
