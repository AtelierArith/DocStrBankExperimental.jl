```Julia
KKH = EntropySystem(Metric,HOUR,kilo,𝟏)
```

キロメートル-キログラム-時間 `UnitSystem` のバリアントである `Metric` システム。

```Julia
julia> boltzmann(KKH) # kg⋅km²⋅h⁻²⋅K⁻¹
1.789321103384932e-22

julia> planckreduced(KKH) # kg⋅km²⋅h⁻¹
3.7964585435261634e-37

julia> lightspeed(KKH) # km⋅hr⁻¹
1.0792528488e9

julia> vacuumpermeability(KKH) # kg⋅km⋅C⁻²
1.2566370614359174e-9

julia> electronmass(KKH) # kg
9.109383701558256e-31

julia> molarmass(KKH) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(KKH) # lm⋅h³⋅kg⁻¹⋅km⁻²
0.014639482383618183
```
