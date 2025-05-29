```Julia
MetricArcminute = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^5*𝟑^3*𝟓^2/τ)
```

標準の `MetricArcminute` システムは、正確な `molarmass` と `vacuumpermeability` に基づいています。

```Julia
julia> boltzmann(MetricArcminute) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(MetricArcminute) # J⋅s⋅amin⁻¹
3.0676250694444446e-38

julia> lightspeed(MetricArcminute) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MetricArcminute) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(MetricArcminute) # kg
9.109383701558256e-31

julia> molarmass(MetricArcminute) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(MetricArcminute) # lm⋅W⁻¹
683.01969009009
```
