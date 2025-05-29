```Julia
illuminance(U::UnitSystem,S::UnitSystem) = luminousflux(U,S)/area(U,S)
illuminance(v::Real,U::UnitSystem,S::UnitSystem) = v/illuminance(U,S)
```

面積あたりの光束または輝度 (lx, lm⋅m⁻², cd⋅m⁻²⋅rad²)、単位変換係数。

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
