```Julia
British = RankineSystem(Metric,ft,slug)
```

British Gravitational `UnitSystem` historically used by Britain and United States.

```Julia
julia> boltzmann(British) # ft⋅lb⋅°R⁻¹
5.657302463819266e-24

julia> planckreduced(British) # ft⋅lb⋅s⋅rad⁻¹
7.778122563903315e-35

julia> lightspeed(British) # ft⋅s⁻¹
9.835710564304461e8

julia> vacuumpermeability(British) # slug⋅ft⋅C⁻²
2.825032496413345e-7

julia> electronmass(British) # slugs
6.241910570978499e-32

julia> molarmass(British) # slug⋅slug-mol⁻¹
1

julia> luminousefficacy(British) # lm⋅s⋅ft⁻¹⋅lb⁻¹
926.0503548878946
```
