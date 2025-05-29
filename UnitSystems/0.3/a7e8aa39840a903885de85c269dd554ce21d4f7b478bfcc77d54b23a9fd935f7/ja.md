```Julia
soundexposure(U::UnitSystem,S::UnitSystem) = pressure(U,S)^2*time(U,S)
soundexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/soundexposure(U,S)
```

`pressure` の二乗と `time` または `soundexposure` (Pa²⋅s, N²⋅m⁻⁴)、単位変換係数。

```Julia
julia> soundexposure(CGS,Metric) # Pa²⋅Ba⁻²
0.009999999999999993

julia> soundexposure(English,Metric) # Pa²⋅ft⁴⋅lb⁻²
2292.519200024031
```
