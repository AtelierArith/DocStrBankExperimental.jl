```Julia
SI1976 = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,8.31432)
```

1976年の標準大気からの普遍的なガス定数`8.31432`を持つ`UnitSystem`を参照してください。

```Julia
julia> boltzmann(SI1976) # J⋅K⁻¹
1.3806253172239044e-23

julia> planckreduced(SI1976) # J⋅s⋅rad⁻¹
1.0545718176461565e-34

julia> lightspeed(SI1976) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(SI1976) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(SI1976) # kg
9.109383701558256e-31

julia> molarmass(SI1976) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(SI1976) # lm⋅W⁻¹
683.01969009009
```
