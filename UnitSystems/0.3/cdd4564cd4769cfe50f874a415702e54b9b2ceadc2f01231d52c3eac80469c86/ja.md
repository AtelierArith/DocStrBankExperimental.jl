```Julia
MetricDegree = MetricSystem(milli,𝟐*τ/𝟏𝟎^7,Rᵤ,𝟏,𝟐^3*𝟑^2*𝟓/τ)
```

標準の `MetricDegree` システムは、正確な `molarmass` と `vacuumpermeability` に基づいています。

```Julia
julia> boltzmann(MetricDegree) # J⋅K⁻¹
1.3806489995254104e-23

julia> planckreduced(MetricDegree) # J⋅s⋅deg⁻¹
1.840575041666667e-36

julia> lightspeed(MetricDegree) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(MetricDegree) # H⋅m⁻¹
1.2566370614359173e-6

julia> electronmass(MetricDegree) # kg
9.109383701558256e-31

julia> molarmass(MetricDegree) # kg⋅mol⁻¹
0.001

julia> luminousefficacy(MetricDegree) # lm⋅W⁻¹
683.01969009009
```
