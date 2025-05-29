```Julia
MTS = EntropySystem(SI2019,𝟏,𝟏,kilo)
```

メートル・トン・秒の `UnitSystem` バリアントの `Metric` システム。

```Julia
julia> boltzmann(MTS) # kJ⋅K⁻¹
1.3806489995254105e-26

julia> planckreduced(MTS) # kJ⋅s⋅rad⁻¹
1.0545718176461564e-37

julia> lightspeed(MTS) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MTS) # kH⋅m⁻¹
1.2566370614359174e-9

julia> electronmass(MTS) # t
9.109383701558256e-34

julia> molarmass(MTS) # t⋅mol⁻¹
1.0e-6

julia> luminousefficacy(MTS) # lm⋅kW⁻¹
683019.6900900899
```
