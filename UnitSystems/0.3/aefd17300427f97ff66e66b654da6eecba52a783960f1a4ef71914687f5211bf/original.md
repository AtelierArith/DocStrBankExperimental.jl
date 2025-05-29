```Julia
InternationalMean = ElectricSystem(Metric,1.00049,1.00034)
```

International `UnitSystem` with mean measurements of `Ωᵢₜ` and `Vᵢₜ`.

```Julia
julia> resistance(InternationalMean,Metric) # Ω⋅Ω⁻¹
1.00049

julia> electricpotential(InternationalMean,Metric) # V⋅V⁻¹
1.00034

julia> boltzmann(InternationalMean) # J⋅K⁻¹
1.3803866950098692e-23

julia> planckreduced(InternationalMean) # J⋅s⋅rad⁻¹
1.0543714633563797e-34

julia> lightspeed(InternationalMean) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(InternationalMean) # H⋅m⁻¹
1.2560216108466024e-6

julia> electronmass(InternationalMean) # kg
9.10765304265832e-31

julia> molarmass(InternationalMean) # kg⋅mol⁻¹
0.0009998100136127059

julia> luminousefficacy(International) # lm⋅W⁻¹
683.1324069249657
```
