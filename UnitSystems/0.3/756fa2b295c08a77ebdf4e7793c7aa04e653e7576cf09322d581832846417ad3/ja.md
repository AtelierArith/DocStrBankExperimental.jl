```Julia
electricflux(U::UnitSystem,S::UnitSystem) = electricpotential(U,S)*length(U,S)
electricflux(v::Real,U::UnitSystem,S::UnitSystem) = v/electricflux(U,S)
```

`electricflux` または `electricpotential` の量を `length` で (V⋅m)、単位変換係数。

```Julia
julia> electricflux(EMU,Metric) # V⋅m⋅abV⁻¹⋅cm⁻¹
1.0000000000000002e-10

julia> electricflux(EMU,ESU) # statV⋅abV⁻¹
3.33564095198152e-11

julia> electricflux(ESU,Metric) # V⋅m⋅statV⁻¹⋅cm⁻¹
2.997924580000001

julia> electricflux(Metric,SI2019) # V⋅V⁻¹
1.0000000002726048
```
