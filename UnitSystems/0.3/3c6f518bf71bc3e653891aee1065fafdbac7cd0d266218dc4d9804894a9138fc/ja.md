```Julia
lapserate(U::UnitSystem,S::UnitSystem) = temperature(U,S)/length(U,S)
lapserate(v::Real,U::UnitSystem,S::UnitSystem) = v/lapserate(U,S)
```

温度勾配 `length` または `lapserate` (K⋅m⁻¹)、単位変換係数。

```Julia
julia> lapserate(Metric,SI2019) # K⋅K⁻¹
0.9999999996562562

julia> lapserate(English,SI2019) # K⋅ft⋅°R⁻¹⋅m⁻¹
1.8226888299363082

julia> lapserate(English,Metric) # K⋅ft⋅°R⁻¹⋅m⁻¹
1.8226888305628464

julia> lapserate(EnglishUS,English) # °R⋅ftUS⋅°R⁻¹⋅ft⁻¹
0.999998
```
