```
ADPCSAFTModel <: SAFTModel
ADPCSAFT(components; 
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
  * `c1`: Single Parameter (`Float64`)
  * `c2`: Single Parameter (`Float64`)
  * `c3`: Single Parameter (`Float64`)
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `theta_c`: Association Parameter (`Float64`)

## Model Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `r_c`: Single Parameter (`Float64`)
  * `c1`: Single Parameter (`Float64`)
  * `c2`: Single Parameter (`Float64`)
  * `c3`: Single Parameter (`Float64`)
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Pair Parameter (`Float64`) - Mixed segment Diameter `[m]`
  * `epsilon`: Pair Parameter (`Float64`) - Mixed reduced dispersion energy`[K]`
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume
  * `theta_c`: Association Parameter (`Float64`)

## Input models

  * `idealmodel`: Ideal Model

## Description

modified Perturbed-Chain SAFT (PC-SAFT) with an association dependent hard sphere diameter.Currently only works for water.

!!! warning "numerically unstable"
    Due to its functional form, DAPT is numerically unstable. Please use `big` Floats for most calculations.


## References

1. Marshall, B. D. (2021). A modified perturbed chain‐statistical associating fluid theory equation of state for water which includes an association dependent hard sphere diameter. AIChE Journal. American Institute of Chemical Engineers, 67(10). [doi:10.1002/aic.17342](https://doi.org/10.1002/aic.17342)
