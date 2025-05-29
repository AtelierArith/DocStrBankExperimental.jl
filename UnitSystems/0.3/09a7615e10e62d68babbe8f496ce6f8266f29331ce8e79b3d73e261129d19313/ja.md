```Julia
electricpotential(U::UnitSystem,S::UnitSystem) = energy(U,S)/charge(U,S)
electricpotential(v::Real,U::UnitSystem,S::UnitSystem) = v/electricpotential(U,S)
```

電圧または `electricpotential` または `energy` あたりの `charge` (V, J⋅C⁻¹)、単位換算係数。

```Julia
julia> electricpotential(EMU,Metric) # V⋅abV⁻¹
1.0e-8

julia> electricpotential(EMU,ESU) # statV⋅abV⁻¹
3.33564095198152e-11

julia> electricpotential(ESU,Metric) # V⋅statV⁻¹
299.79245800000007

julia> electricpotential(Metric,SI2019) # V⋅V⁻¹
1.0000000002726048
```
