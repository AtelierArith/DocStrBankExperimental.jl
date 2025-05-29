```
ConstRSP(solvents::Array{String,1},
    ions::Array{String,1};
    userlocations::Vector{String}=[],
    value::Float64 = 78.38484961,
    verbose::Bool=false)

ConstRSP(val::Float64)
```

## Input parameters

  * `value::Float64`: Constant Relative Static Permittivity `[-]`

## Description

This function is used to create a constant Relative Static Permittivity model, given by `value`.
