```Julia
magneticmoment(U::UnitSystem,S::UnitSystem) = magneticflux(U,S)*length(U,S)
magneticmoment(v::Real,U::UnitSystem,S::UnitSystem) = v/magneticmoment(U,S)
```

`magneticmoment` または `magneticflux` の量を `length` で割ったもの (Wb⋅m または T⋅m³)、単位変換係数。

```Julia
julia> magneticmoment(EMU,Metric) # Wb⋅m⋅Mx⁻¹⋅cm⁻¹
1.0000000000000002e-10

julia> magneticmoment(ESU,Metric) # Wb⋅m⋅statWb⁻¹⋅cm⁻¹
2.997924580000001

julia> magneticmoment(Metric,SI2019) # Wb⋅Wb⁻¹
1.0000000002726048
```
