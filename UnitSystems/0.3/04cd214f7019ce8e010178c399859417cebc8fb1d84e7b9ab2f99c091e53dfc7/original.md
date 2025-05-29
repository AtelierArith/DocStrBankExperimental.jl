```Julia
IPS = RankineSystem(Metric,ft/𝟐^2/𝟑,lb*g₀*𝟐^2*𝟑/ft)
```

British Gravitational `UnitSystem` historically used in the United States of America.

```Julia
julia> boltzmann(IPS) # in⋅lb⋅°R⁻¹
6.788762956583119e-23

julia> planckreduced(IPS) # in⋅lb⋅s⋅rad⁻¹
9.333747076683978e-34

julia> lightspeed(IPS) # in⋅s⁻¹
1.1802852677165354e10

julia> vacuumpermeability(IPS) # slinch⋅in⋅C⁻²
2.825032496413345e-7

julia> electronmass(IPS) # slinch
5.201592142482083e-33

julia> molarmass(IPS) # slinch⋅slinch-mol⁻¹
1

julia> luminousefficacy(IPS) # lm⋅s⋅in⁻¹⋅lb⁻¹
77.17086290732456
```
