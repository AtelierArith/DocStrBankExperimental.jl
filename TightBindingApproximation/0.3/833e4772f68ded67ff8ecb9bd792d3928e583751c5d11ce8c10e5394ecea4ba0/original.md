```
FermiSurfaceData{S<:ReciprocalScatter} <: Data
```

Data of Fermi surface, including:

1. `values::S`: points of the Fermi surface.
2. `weights::Matrix{Float64}`: weights of several certain sets of orbitals projected onto the Fermi surface.
