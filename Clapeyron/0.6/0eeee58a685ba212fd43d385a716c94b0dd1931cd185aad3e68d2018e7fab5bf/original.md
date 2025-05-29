```
GCMSABorn(solvents::Array{String,1},
     ions::Array{String,1};
     RSPmodel=ConstRSP,
     SAFTlocations=String[],
     userlocations=String[],
     verbose=false)
```

## Input parameters

  * `sigma`: Single Parameter (`Float64`) - Hard-sphere diameter `[m]`
  * `sigma_born`: Single Parameter (`Float64`) - Born Diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `RSPmodel`: Relative Static Permittivity Model

## Description

This function is used to create a group-contribution Mean Spherical Approximation-Born model used in SAFT-gamma E Mie
