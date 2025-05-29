```Julia
Gravitational = EntropySystem(Metric,𝟏,𝟏,g₀)
```

標準の `Gravitational` システムは `hyl` および `kilopond` 単位に基づいています。

```Julia
julia> boltzmann(Gravitational) # kgf⋅m⋅K⁻¹
1.4078701692478171e-24

julia> planckreduced(Gravitational) # kgf⋅m⋅s⋅rad⁻¹
1.0753639802033891e-35

julia> lightspeed(Gravitational) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(Gravitational) # H⋅m⁻¹
1.2814131853751459e-7

julia> electronmass(Gravitational) # hyl
9.288986250715847e-32

julia> molarmass(Gravitational) # hyl⋅mol⁻¹
0.00010197162129779284

julia> luminousefficacy(Gravitational) # lm⋅s⋅m⁻¹⋅kgf⁻¹
6698.135043821981
```
