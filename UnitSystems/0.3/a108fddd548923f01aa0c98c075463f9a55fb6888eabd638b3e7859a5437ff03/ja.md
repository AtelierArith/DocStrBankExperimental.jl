```Julia
luminousexposure(U::UnitSystem,S::UnitSystem) = illuminance(U,S)*time(U,S)
luminousexposure(v::Real,U::UnitSystem,S::UnitSystem) = v/luminousexposure(U,S)
```

時間に沿った `luminance` の統合 (lx⋅s, lm⋅s⋅m⁻², cd⋅s⋅m⁻²⋅sr)、単位変換係数。

```Julia
julia> luminousexposure(CGS,Metric) # lx⋅ph⁻¹
9999.999999999996

julia> luminousexposure(IAU,Metric) # s⋅au²⋅day⁻¹⋅m⁻²
3.8606721115850325e-18

julia> luminousexposure(English,Metric) # ft²⋅m⁻²
10.763910416709722
```
