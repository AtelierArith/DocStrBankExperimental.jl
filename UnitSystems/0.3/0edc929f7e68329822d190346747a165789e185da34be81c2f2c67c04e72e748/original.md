```Julia
Cosmological = AstronomicalSystem(Metric,lc/𝘤,lc,mc)
```

Cosmological scale `UnitSystem` defined by `darkenergydensity`.

```Julia
julia> boltzmann(Cosmological)
1.0

julia> planckreduced(Cosmological)
2.8881439991247135e-122

julia> lightspeed(Cosmological)
1.0

julia> vacuumpermeability(Cosmological)
12.566370614359172

julia> electronmass(Cosmological)
3.565930258299465e-83

julia> molarmass(Cosmological)
1

julia> luminousefficacy(Cosmological)
1

julia> hubble(Cosmological)
3.4872349617265916

julia> cosmological(Cosmological)
25.132741228718352
```
