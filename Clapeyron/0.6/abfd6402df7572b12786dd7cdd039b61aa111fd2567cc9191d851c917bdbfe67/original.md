```
ePCSAFT(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = pharmaPCSAFT,
    ionmodel::IonModel = DH,
    RSPmodel::RSPModel = ConstRSP,
    userlocations::Vector{String} = [],
    ideal_userlocations::Vector{String} = [],
    assoc_options::AssocOptions = AssocOptions(),
    verbose::Bool = false,
    reference_state = nothing)
```

## Description

This function is used to create an ePCSAFT model which is a combination of the PC-SAFT and Debye-Hückel model. It is based on the ePC-SAFT Revised variant.

## Input parameters

### PC-SAFT Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

### Debye-Hückel Parameters

  * `sigma`: Single Parameter (`Float64`) - Diameter of closest approach `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `idealmodel`: Ideal Model
  * `neutralmodel`: Neutral EoS Model
  * `ionmodel`: Ion Model

## References

1. Held, C., Reschke, T., Mohammad, S., Luza, A., Sadowski, G. (2014). ePC-SAFT Revised. Chemical Engineering Research and Design, 92(12), 2884-2897.
