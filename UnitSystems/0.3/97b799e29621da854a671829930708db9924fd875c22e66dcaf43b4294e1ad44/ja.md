```Julia
angularfrequency(U::UnitSystem,S::UnitSystem) = angle(U,S)/time(U,S)
angularfrequency(v::Real,U::UnitSystem,S::UnitSystem) = v/angularfrequency(U,S)
```

円周ラジアン周波数 (rad⋅Hz または rad⋅s⁻¹)、単位変換係数。

```Julia
julia> angularfrequency(IAU,Metric) day⋅s⁻¹
1.1574074074074073e-5
```
