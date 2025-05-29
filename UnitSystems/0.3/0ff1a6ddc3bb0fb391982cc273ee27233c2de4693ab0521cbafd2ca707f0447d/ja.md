```Julia
permeability(U::UnitSystem,S::UnitSystem) = permeability(S)/permeability(U)
permeability(v::Real,U::UnitSystem,S::UnitSystem) = v/permeability(U,S)
```

磁気の `permeability` または `inductance` の長さあたり (H⋅m⁻¹)、単位変換係数。

```Julia
julia> permeability(EMU,Metric) # H⋅cm⋅abH⁻¹⋅m⁻¹
1.2566370614359173e-6

julia> permeability(ESU,Metric) # H⋅cm⋅statH⁻¹⋅m⁼¹
1.1294090667581472e15

julia> permeability(Metric,SI2019) # H⋅H⁻¹
1.0000000005452097
```
