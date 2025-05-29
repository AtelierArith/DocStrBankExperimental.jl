```Julia
electricdipolemoment(U::UnitSystem,S::UnitSystem) = charge(U,S)*length(U,S)
electricdipolemoment(v::Real,U::UnitSystem,S::UnitSystem) = v/electricdipolemoment(U,S)
```

電気双極子モーメントまたは `electricdipolemoment` (C⋅m)、単位変換係数。

```Julia
julia> electricdipolemoment(EMU,Metric) # C⋅m⋅abC⁻¹⋅cm⁻¹
0.10000000000000002

julia> electricdipolemoment(ESU,Metric) # C⋅m⋅statC⁻¹⋅cm⁼¹
3.3356409519815207e-12

julia> electricdipolemoment(Metric,SI2019) # C⋅C⁻¹
0.9999999997273952
```
