```Julia
permeance(U::UnitSystem,S::UnitSystem) = 1/reluctance(U,S)
permeance(v::Real,U::UnitSystem,S::UnitSystem) = v/permeance(U,S)
```

磁気の `permeance` または磁気導電率 (H, Mx⋅Gb⁻¹)、単位変換係数。

```Julia
julia> permeance(EMU,Metric) # abH⋅H⁻¹
1.256637061435917e-8

julia> permeance(ESU,Metric) # statH⋅H⁻¹
1.129409066758147e13

julia> permeance(Metric,SI2019) # H⋅H⁻¹
1.0000000005452097
```
