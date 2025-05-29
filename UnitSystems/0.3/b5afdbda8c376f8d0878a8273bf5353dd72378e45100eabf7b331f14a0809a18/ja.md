```Julia
temperature(U::UnitSystem,S::UnitSystem) = mass(U,S)*speed(U,S)^2/entropy(U,S)
temperature(v::Real,U::UnitSystem,S::UnitSystem) = v/temperature(U,S)
```

熱力学エネルギーまたは `temperature` (K) の測定スケール、単位換算係数。

```Julia
julia> temperature(Metric,SI2019) # K⋅K⁻¹
0.9999999996562562

julia> temperature(English,SI2019) # K⋅°R⁻¹
0.5555555553645868

julia> temperature(English,Metric) # K⋅°R⁻¹
0.5555555555555556

julia> temperature(PlanckGauss,Metric) # K⋅TP⁻¹
1.4167839395467477e32
```
