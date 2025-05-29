```Julia
radiance(U::UnitSystem,S::UnitSystem) = irradiance(U,S)/solidangle(U,S)
radiance(v::Real,U::UnitSystem,S::UnitSystem) = v/radiance(U,S)
```

放射輝度または `irradiance` あたりの `solidangle` (W⋅m⁻²⋅sr⁻¹, kg⋅s⁻³⋅sr⁻¹)、単位変換係数。

```Julia
julia> radiance(CGS,Metric) # kg⋅g⁻¹
0.0009999999999999996

julia> radiance(CGS,English) # lb⋅g⁻¹
6.852176585679174e-5

julia> radiance(English,Metric) # kg⋅lb⁻¹
14.593902937206364
```
