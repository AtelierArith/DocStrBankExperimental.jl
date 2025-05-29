```Julia
Conventional = ConventionalSystem(RK1990,KJ2014)
```

1990年調整の`josephson`および`klitzing`定数を持つ従来の電子`UnitSystem`。

```Julia
julia> josephson(Conventional) # Hz⋅V⁻¹
4.8359789999999994e14

julia> klitzing(Conventional) # Ω
25812.807

julia> boltzmann(Conventional) # J⋅K⁻¹
1.3806487295581143e-23

julia> planckreduced(Conventional) # J⋅s⋅rad⁻¹
1.054571611438857e-34

julia> lightspeed(Conventional) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(Conventional) # H⋅m⁻¹
1.2566370397608662e-6

julia> electronmass(Conventional) # kg
9.109381920341098e-31

julia> molarmass(Conventional) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(Conventional) # lm⋅W⁻¹
683.0198236454073
```
