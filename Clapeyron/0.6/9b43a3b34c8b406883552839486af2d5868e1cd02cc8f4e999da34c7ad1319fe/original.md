```
Schreckenberg(solvents::Array{String,1},
     ions::Array{String,1};
     userlocations::Vector{String}=[],
     verbose::Bool=false)
```

## Input parameters

  * `d_T::Float64`: Single Parameter - Temperature dependent dielectric constant `[-]`
  * `d_V::Float64`: Single Parameter - Volume dependent dielectric constant `[-]`
  * `charge::Float64`: Single Parameter - Charge `[-]`

## Description

This function is used to create a Schreckenberg model. The Schreckenberg term estimates the dielectric constant for a mixture of solvents.

## References

1. Schreckenberg, J., Dufal, S., Haslam, A.J., Adjiman, C.S., Jackson, G., Galindo, A. (2014). Modelling of the thermodynamic and solvation properties of electrolyte solutions with the statistical associating fluid theory for potentials of variable range. Molecular Physics, 112(17), 2339-2364.
