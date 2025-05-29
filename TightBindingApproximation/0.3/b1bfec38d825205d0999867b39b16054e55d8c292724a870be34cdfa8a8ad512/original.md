```
EnergyBandsData{R<:ReciprocalSpace, W<:Union{Array{Float64, 3}, Nothing}} <: Data
```

Data of energy bands, including:

1. `reciprocalspace::R`: reciprocal space on which the energy bands are computed.
2. `values::Matrix{Float64}`: eigen energies of bands with each column storing the values on the same reciprocal point.
3. `weights::W`: if not `nothing`, weights of several certain sets of orbitals projected onto the energy bands.
