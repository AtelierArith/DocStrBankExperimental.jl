```Julia
molarenergy(U::UnitSystem,S::UnitSystem) = energy(U,S)/molaramount(U,S)
molarenergy(v::Real,U::UnitSystem,S::UnitSystem) = v/molarenergy(U,S)
```

ギブス自由 `エネルギー` あたり `モル` または `molarenergy` (J⋅mol⁻¹)、単位変換係数。

```Julia
julia> molarenergy(CGS,Metric) # J⋅erg⁻¹
1.0000000000000001e-7

julia> molarenergy(English,SI2019) # J⋅slug-mol⋅ft⁻¹⋅lb⁻¹⋅mol⁻¹
0.002989066918972526
```
