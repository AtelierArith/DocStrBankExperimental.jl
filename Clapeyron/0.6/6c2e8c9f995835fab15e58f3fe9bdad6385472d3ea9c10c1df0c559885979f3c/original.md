```
MSA(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## Input parameters

  * `sigma`: Single Parameter (`Float64`) - Hard-sphere diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `RSPmodel`: Relative Static Permittivity Model

## Description

This function is used to create a Mean Spherical Approximation model. The MSA term gives the excess Helmholtz energy to account for the electrostatic interactions between ions in solution.

## References

1. Blum, L. (1974). Solution of a model for the solvent‐electrolyte interactions in the mean spherical approximation, 61, 2129–2133.
