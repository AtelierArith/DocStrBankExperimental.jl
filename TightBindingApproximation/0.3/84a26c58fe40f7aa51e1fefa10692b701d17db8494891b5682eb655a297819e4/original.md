```
InelasticNeutronScatteringSpectraData{R<:ReciprocalSpace} <: Data
```

Data of inelastic neutron scattering spectra, including:

1. `reciprocalspace::R`: reciprocal space on which the inelastic neutron scattering spectra are computed
2. `energies::Vector{Float64}`: energy sample points.
3. `values::Matrix{Float64}`: rescaled intensity of inelastic neutron scattering spectra.
