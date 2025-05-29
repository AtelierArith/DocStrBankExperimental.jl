```Julia
catalysis(U::UnitSystem,S::UnitSystem) = molaramount(U,S)/time(U,S)
catalysis(v::Real,U::UnitSystem,S::UnitSystem) = v/catalysis(U,S)
```

触媒活性または `molaramount` あたりの `time` (kat, mol⋅s⁻¹)、単位変換係数。

```Julia
julia> catalysis(English,Metric) # kat⋅s⋅lb-mol⁻¹
453.59237
```
