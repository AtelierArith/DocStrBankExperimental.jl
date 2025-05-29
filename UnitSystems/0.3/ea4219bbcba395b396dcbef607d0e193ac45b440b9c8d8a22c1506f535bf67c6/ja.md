```Julia
CGSm = GaussSystem(Metric,𝟏,𝟐*τ)
```

センチメートル-グラム-秒 `UnitSystem` のバリアントで、`EMU`（非合理化）。

```Julia
julia> boltzmann(CGSm) # erg⋅K⁻¹
1.3806489995254102e-16

julia> planckreduced(CGSm) # erg⋅s⋅rad⁻¹
1.0545718176461563e-27

julia> lightspeed(CGSm) # cm⋅s⁻¹
2.99792458e10

julia> vacuumpermeability(CGSm) # abH⋅cm⁻¹
1

julia> electronmass(CGSm) # g
9.109383701558256e-28

julia> molarmass(CGSm) # g⋅mol⁻¹
1

julia> luminousefficacy(CGSm) # lm⋅s⋅erg⁻¹
6.8301969009009e-5

julia> rationalization(CGSm)
12.566370614359172
```
