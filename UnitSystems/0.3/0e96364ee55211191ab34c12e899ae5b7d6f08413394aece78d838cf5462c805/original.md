```Julia
avogadro(U::UnitSystem) = molargas(x)/boltzmann(x) # Mᵤ/dalton(x)
```

Avogadro `NA` is `molarmass(x)/dalton(x)` number of atoms in a 12 g sample of C₁₂.

```Julia
julia> avogadro(SI2019) # mol⁻¹
6.02214076e23

julia> avogadro(Metric) # mol⁻¹
6.022140762070074e23

julia> avogadro(CODATA) # mol⁻¹
6.0221408628723465e23

julia> avogadro(Conventional) # mol⁻¹
6.022141939618732e23

julia> avogadro(English) # lb-mol⁻¹
2.731597100740971e26

julia> avogadro(British) # slug-mol⁻¹
8.788653775584461e27
```
