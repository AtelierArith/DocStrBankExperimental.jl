```
LinMixRSP(solvents::Array{String,1},
     ions::Array{String,1};
     userlocations::Vector{String}=[],
     verbose::Bool=false)
```

## Input parameters

  * `dielectric_constant::Float64`: Constant Relative Static Permittivity `[-]`

## Description

This function is used to create a Linear Mixing-Rule Relative Static Permittivity model, for a mixture of solvents, where each solvent has a `dielectric_constant`.
