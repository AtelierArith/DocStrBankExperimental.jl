```
Born(solvents::Array{String,1},
    salts::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## Input parameters

  * `sigma_born`: Single Parameter (`Float64`) - Born Diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `RSPmodel`: Relative Static Permittivity Model

## Description

This function is used to create a Born model. The Born term gives the excess Helmholtz energy to account for the electrostatic interactions between ions in solution.

## References

1. Born, M. (1920). Z. Phys. 1, 45.
