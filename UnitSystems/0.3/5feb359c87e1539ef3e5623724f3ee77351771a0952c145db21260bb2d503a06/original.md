```Julia
permeance(U::UnitSystem,S::UnitSystem) = 1/reluctance(U,S)
permeance(v::Real,U::UnitSystem,S::UnitSystem) = v/permeance(U,S)
```

Magnetic `permeance` or magnetic conductance (H, Mx⋅Gb⁻¹), unit conversion factor.

```Julia
julia> permeance(EMU,Metric) # abH⋅H⁻¹
1.256637061435917e-8

julia> permeance(ESU,Metric) # statH⋅H⁻¹
1.129409066758147e13

julia> permeance(Metric,SI2019) # H⋅H⁻¹
1.0000000005452097
```
