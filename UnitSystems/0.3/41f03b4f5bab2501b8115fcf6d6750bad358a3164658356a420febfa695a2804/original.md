```Julia
dalton(U::UnitSystem) = molarmass(U)/avogadro(U)
```

Atomic mass unit `Da` of 1/12 of the C₁₂ carbon-12 atom's mass  (kg or slugs).

```Julia
julia> dalton(Metric) # kg
1.6605390666030467e-27

julia> dalton(Hartree) # mₑ
1822.8884862090001

julia> dalton(QCD) # mₚ
0.9927760978617821

julia> dalton(Metric)*lightspeed(Metric)^2 # J
1.4924180856042896e-10

julia> dalton(SI2019)*lightspeed(SI2019)^2/elementarycharge(SI2019) # eV⋅𝘤⁻²
9.314941024188533e8

julia> dalton(British) # lb
1.1378306911782951e-28
```
