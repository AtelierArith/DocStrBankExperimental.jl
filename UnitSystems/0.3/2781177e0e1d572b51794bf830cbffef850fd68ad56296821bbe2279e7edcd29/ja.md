```Julia
stagnance(U::UnitSystem,S::UnitSystem) = lightspeed(U)/lightspeed(S)
stagnance(v::Real,U::UnitSystem,S::UnitSystem) = v/stagnance(U,S)
```

スタグナンスまたは `時間` あたり `長さ` (s⋅m⁻¹)、単位変換係数。

```Julia
julia> stagnance(CGS,Metric) # cm⋅m⁻¹
100.0

julia> stagnance(IAU,Metric) # au⋅s⋅day⁻¹⋅m⁻¹
5.775483273639937e-7

julia> stagnance(English,Metric) # ft⋅m⁻¹
3.280839895013123

julia> stagnance(Survey,English) # ftUS⋅ft⁻¹
0.9999980000000002
```
