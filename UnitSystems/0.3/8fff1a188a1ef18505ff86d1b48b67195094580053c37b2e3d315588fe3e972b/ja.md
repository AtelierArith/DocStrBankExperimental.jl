```Julia
volume(U::UnitSystem,S::UnitSystem) = length(U,S)^3
volume(v::Real,U::UnitSystem,S::UnitSystem) = v/volume(U,S)
```

三次元形状の範囲または `volume` (m³)、単位変換係数。

```Julia
julia> volume(CGS,Metric) # m³⋅cm⁻³
1.0000000000000006e-6

julia> volume(English,Metric) # m³⋅ft⁻³
0.028316846592000004

julia> volume(Survey,English) # ft³⋅ftUS⁻³
1.0000060000239999
```
