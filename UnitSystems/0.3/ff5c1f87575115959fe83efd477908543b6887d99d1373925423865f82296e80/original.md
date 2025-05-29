```Julia
MetricArcsecond = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^7*𝟑^4*3/τ)
```

Standard `MetricArcsecond` system based on exact `molarmass` and `vacuumpermeability`.

```Julia
julia> boltzmann(MetricArcsecond) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(MetricArcsecond) # J⋅s⋅asec⁻¹
5.112708449074075e-40

julia> lightspeed(MetricArcsecond) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MetricArcsecond) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(MetricArcsecond) # kg
9.109383701558256e-31

julia> molarmass(MetricArcsecond) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(MetricArcsecond) # lm⋅W⁻¹
683.01969009009
```
