```
MSABorn(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## Input parameters

  * `sigma`: Single Parameter (`Float64`) - Hard-sphere diameter `[m]`
  * `sigma_born`: Single Parameter (`Float64`) - Born Diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `RSPmodel`: Relative Static Permittivity Model

## Description

This function is used to create a Mean Spherical Approximation-Born model. The MSA-Born term gives the excess Helmholtz energy to account for the electrostatic interactions between ions in solution.

## References

1. Blum, L. (1974). Solution of a model for the solvent‐electrolyte interactions in the mean spherical approximation, 61, 2129–2133.
2. Born, M. (1920). Z. Phys. 1, 45.
