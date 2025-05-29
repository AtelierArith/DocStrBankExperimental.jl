```Julia
MetricGradian = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^4*𝟓^2/τ)
```

Standard `MetricGradian` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(MetricGradian) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(MetricGradian) # J⋅s⋅gon⁻¹
1.6565175375e-36

julia> lightspeed(MetricGradian) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MetricGradian) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(MetricGradian) # kg
9.109383701558256e-31

julia> molarmass(MetricGradian) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(MetricGradian) # lm⋅W⁻¹
683.01969009009
```
