```Julia
eddington(U::UnitSystem) = mass(𝟏,U,Cosmological)
```

エディントンによって推定された `宇宙` における陽子の近似数（kgまたはlb）。

```Julia
julia> 𝟐^2^2^3/α # mₚ
0.0

julia> eddington(QCD) # mₚ
1.5272789483733458e79

julia> eddington(Metric) # kg
2.554560252645652e52

julia> eddington(IAU) # M☉
1.2847255938700031e22

julia> eddington(Cosmological)
1
```
