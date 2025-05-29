```Julia
SI2019 = MetricSystem(Mᵤ,μ₀)
```

Systeme International d'Unites based on approximate `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(SI2019) # J⋅K⁻¹
1.380649e-23

julia> planckreduced(SI2019) # J⋅s⋅rad⁻¹
1.0545718176461565e-34

julia> lightspeed(SI2019) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(SI2019) # H⋅m⁻¹
1.256637062121048e-6

julia> electronmass(SI2019) # kg
9.109383701558256e-31

julia> molarmass(SI2019) # kg⋅mol⁻¹
0.000999999999656256

julia> luminousefficacy(SI2019) # lm⋅W⁻¹
683.01969009009
```
