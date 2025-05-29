```Julia
magneton(U::UnitSystem) = elementarycharge(U)*planckreduced(U)*lorentz(U)/2electronmass(U)
```

Bohr magneton `μB` natural unit for expressing magnetic moment of electron (J⋅T⁻¹).

```Julia
julia> magneton(SI2019) # J⋅T⁻¹
9.274010078302855e-24

julia> magneton(Metric) # J⋅T⁻¹
9.274010080830994e-24

julia> magneton(CODATA) # J⋅T⁻¹
9.274010001369277e-24

julia> magneton(Conventional) # J⋅T⁻¹
9.274009254108318e-24

julia> magneton(International) # J⋅T⁻¹
9.275539787691068e-24

julia> magneton(ESU) # statA⋅cm²
2.7802782776491024e-10

julia> magneton(SI2019)/elementarycharge(SI2019) # eV⋅T⁻¹
5.788381806036784e-5

julia> magneton(Hartree) # 𝘤⋅ħ⋅mₑ⁻¹
0.5
```
