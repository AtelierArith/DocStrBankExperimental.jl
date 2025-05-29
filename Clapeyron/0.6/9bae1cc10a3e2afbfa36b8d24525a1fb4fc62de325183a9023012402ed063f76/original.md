```
DHBorn(solvents::Array{String,1},
    ions::Array{String,1};
    RSPmodel = ConstRSP,
    userlocations = String[],
    RSPmodel_userlocations = String[],
    verbose = false)
```

## Input parameters

  * `sigma`: Single Parameter (`Float64`) - Diameter of closest approach `[m]`
  * `sigma_born`: Single Parameter (`Float64`) - Born Diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `RSPmodel`: Relative Static Permittivity Model

## Description

This function is used to create a Debye-Hückel-Born model. The Debye-Hückel-Born term gives the excess Helmholtz energy to account for the electrostatic interactions between ions in solution.

## References

1. Debye, P., Huckel, E. (1923). Phys. Z. 24, 185.
2. Born, M. (1920). Z. Phys. 1, 45.
