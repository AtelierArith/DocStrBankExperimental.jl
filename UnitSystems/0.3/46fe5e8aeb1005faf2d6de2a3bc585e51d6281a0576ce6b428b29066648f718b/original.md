```Julia
MetricTurn = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟏/τ)
```

Standard `MetricTurn` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(MetricTurn) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(MetricTurn) # J⋅s⋅τ⁻¹
6.62607015e-34

julia> lightspeed(MetricTurn) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MetricTurn) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(MetricTurn) # kg
9.109383701558256e-31

julia> molarmass(MetricTurn) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(MetricTurn) # lm⋅W⁻¹
683.01969009009
```
