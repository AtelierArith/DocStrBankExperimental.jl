```Julia
electricpolarizability(U::UnitSystem,S::UnitSystem) = electricdipolemoment(U,S)/electricfield(U,S)
electricpolarizability(v::Real,U::UnitSystem,S::UnitSystem) = v/electricpolarizability(U,S)
```

極化率または `electricdipolemoment` あたりの `electricfield` (C⋅m²⋅V⁻¹)、単位換算係数。

```Julia
julia> electricpolarizability(EMU,Metric) # C⋅m²⋅abV⋅abC⁻¹⋅cm⁻²⋅V⁻¹
100000.00000000004

julia> electricpolarizability(ESU,Metric) # C⋅m²⋅statV⋅statC⁻¹⋅cm⁼²⋅V⁻¹
1.1126500560536184e-16

julia> electricpolarizability(Metric,Gauss) # D⋅cm²⋅V⁻¹⋅C⁻¹⋅m⁻²⋅abV⁻¹
8.987551787368173e15

julia> electricpolarizability(Metric,SI2019) # C⋅V⋅C⁻¹⋅V⁻¹
0.9999999994547903
```
