```Julia
magnetostatic(U::UnitSystem) = lorentz(U)*biotsavart(U) # electrostatic(U)/lightspeed(U)^2
```

アンペールの法則による力のための磁気比例定数 `kₘ` (N·s²⋅C⁻²)。

```Julia
julia> magnetostatic(Metric) # H⋅m⁻¹
1.0000000000000001e-7

julia> magnetostatic(CODATA) # H⋅m⁻¹
1.0000000003978213e-7

julia> magnetostatic(SI2019) # H⋅m⁻¹
1.00000000054521e-7

julia> magnetostatic(Conventional) # H⋅m⁻¹
9.999999827515425e-8

julia> magnetostatic(International) # H⋅m⁻¹
9.995052449037728e-8

julia> magnetostatic(EMU) # abH⋅m⁻¹
1.0

julia> magnetostatic(ESU) # statH⋅m⁻¹
1.1126500560536182e-21

julia> magnetostatic(HLU) # hlH⋅m⁻¹
8.854187817620392e-23
```
