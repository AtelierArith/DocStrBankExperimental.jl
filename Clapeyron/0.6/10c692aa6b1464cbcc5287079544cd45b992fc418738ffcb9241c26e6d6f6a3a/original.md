```
DAPTModel <: SAFTModel
DAPT(components; 
idealmodel = BasicIdeal,
userlocations = String[],
ideal_userlocations = String[],
reference_state = nothing,
verbose = false,
assoc_options = AssocOptions())
```

## Input parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `r_c`: Single Parameter (`Float64`)
  * `lambda`: Single Parameter (`Float64`)
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `theta_c`: Association Parameter (`Float64`)

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `r_c`: Single Parameter (`Float64`)
  * `lambda`: Single Parameter (`Float64`)
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `theta_c`: Association Parameter (`Float64`)

## Input models

  * `idealmodel`: Ideal Model

## Description

Doubly-Associated Perturbation Theory model. Currently only works for water.

!!! warning "numerically unstable"
    Due to its functional form, DAPT is numerically unstable. Please use `big` Floats for most calculations.


## References

1. Marshall, B. D. (2019). A doubly associated reference perturbation theory for water. Fluid Phase Equilibria, 500(112252), 112252. [doi:10.1016/j.fluid.2019.112252](https://doi.org/10.1016/j.fluid.2019.112252)
