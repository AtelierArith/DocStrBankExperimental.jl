```Julia
Metric = MetricSystem(milli,𝟐*τ/𝟏𝟎^7)
```

Standard `Metric` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(Metric) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(Metric) # J⋅s⋅rad⁻¹
1.0545718176461565e-34

julia> lightspeed(Metric) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(Metric) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(Metric) # kg
9.109383701558256e-31

julia> molarmass(Metric) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(Metric) # lm⋅W⁻¹
683.01969009009
```
