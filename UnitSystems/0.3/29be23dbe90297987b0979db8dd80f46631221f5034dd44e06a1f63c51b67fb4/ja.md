```Julia
CGSe = GaussSystem(Metric,(𝟏𝟎*𝘤)^-2,𝟐*τ)
```

センチメートル-グラム-秒 `UnitSystem` のバリアントで、`ESU`（非合理化）。

```Julia
julia> boltzmann(CGSe) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(CGSe) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(CGSe) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(CGSe) # statH⋅cm⁻¹
1.1126500560536182e-21

julia> electronmass(CGSe) # g
9.109383701558256e-28

julia> molarmass(CGSe) # g⋅mol⁻¹
1

julia> luminousefficacy(CGSe) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(CGSe)
12.566370614359172
```
