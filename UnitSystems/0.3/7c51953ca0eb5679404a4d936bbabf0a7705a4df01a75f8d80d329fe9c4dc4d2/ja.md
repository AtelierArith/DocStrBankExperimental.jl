```Julia
International = ElectricSystem(Metric,1.000495,1.00033)
```

国際的な `UnitSystem` は、アメリカ合衆国の測定値 `Ωᵢₜ` と `Vᵢₜ` を使用しています。

```Julia
julia> resistance(International,Metric) # Ω⋅Ω⁻¹
1.0004949999999997

julia> electricpotential(International,Metric) # V⋅V⁻¹
1.0003299999999997

julia> boltzmann(International) # J⋅K⁻¹
1.3804211924652808e-23

julia> planckreduced(International) # J⋅s⋅rad⁻¹
1.0543978133151816e-34

julia> lightspeed(International) # m⋅s⁻¹
2.99792458e8

julia> vacuumpermeability(International) # H⋅m⁻¹
1.2560153338456639e-6

julia> electronmass(International) # kg
9.107880653411075e-31

julia> molarmass(International) # kg⋅mol⁻¹
0.000999835000017957

julia> luminousefficacy(International) # lm⋅W⁻¹
683.1324069249657
```
