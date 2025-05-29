```Julia
elementarycharge(U::UnitSystem) = √(𝟐*planck(U)*finestructure(U)/vacuumimpedance(U))
```

Quantized elementary charge `𝘦` of a proton or electron `2/(klitzing(U)*josephson(U))` (C).

```Julia
julia> elementarycharge(SI2019) # C
1.602176634e-19

julia> elementarycharge(Metric) # C
1.6021766344367608e-19

julia> elementarycharge(CODATA) # C
1.6021766207089657e-19

julia> elementarycharge(Conventional) # C
1.6021764916122712e-19

julia> elementarycharge(International) # C
1.6024409063717046e-19

julia> elementarycharge(EMU) # abC
1.602176634436761e-20

julia> elementarycharge(ESU) # statC
4.803204713879641e-10

julia> elementarycharge(Hartree) # 𝘦
1.0
```
