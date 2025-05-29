```Julia
CODATA = ConventionalSystem(RK2014,KJ2014,Rᵤ2014)
```

Reference `UnitSystem` based on Committee on Data of the International Science Council.

```Julia
julia> josephson(CODATA) # Hz⋅V⁻¹
4.8359785250000006e14

julia> klitzing(CODATA) # Ω
25812.8074555

julia> boltzmann(CODATA) # J⋅K⁻¹
1.3806485084499174e-23

julia> planckreduced(CODATA) # J⋅s⋅rad⁻¹
1.0545717999940896e-34

julia> lightspeed(CODATA) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(CODATA) # H⋅m⁻¹
1.2566370619358342e-6

julia> electronmass(CODATA) # kg
9.10938354907983e-31

julia> molarmass(CODATA) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(CODATA) # lm⋅W⁻¹
683.019701522891
```
