```
COSTALD(components; 
            userlocations::Vector{String}=String[], 
            verbose::Bool=false)
```

## Input parameters

  * `Tc`: Single Parameter (Float64) - Critical Temperature `[K]`
  * `Vc`: Single Parameter (`Float64`) - Critical Volume `[m³/mol]`
  * `acentricfactor`: Single Parameter (`Float64`) - Acentric Factor

## Description

COSTALD Equation of State for saturated liquids. it is independent of the pressure.

## Model Construction Examples

```julia
# Using the default database
model = COSTALD("water") #single input
model = COSTALD(["water","ethanol"]) #multiple components

# User-provided parameters, passing files or folders
model = COSTALD(["neon","hydrogen"]; userlocations = ["path/to/my/db","critical.csv"])

# User-provided parameters, passing parameters directly

model = COSTALD(["neon","hydrogen"];
        userlocations = (;Tc = [44.492,33.19],
                        Vc = [4.25e-5, 6.43e-5],
                        acentricfactor = [-0.03,-0.21])
                    )
```

## References

Hankinson, R. W., & Thomson, G. H. (1979). A new correlation for saturated densities of liquids and their mixtures. AIChE Journal. American Institute of Chemical Engineers, 25(4), 653–663. [doi:10.1002/aic.690250412](https://doi.org/doi:10.1002/aic.690250412)
