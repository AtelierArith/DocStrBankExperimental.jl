```Julia
luminance(U::UnitSystem,S::UnitSystem) = luminousintensity(U,S)/area(U,S)
luminance(v::Real,U::UnitSystem,S::UnitSystem) = v/luminance(U,S)
```

面積あたりの光度または輝度 (cd⋅m⁻², lm⋅m⁻²⋅rad⁻²)、単位変換係数。

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
