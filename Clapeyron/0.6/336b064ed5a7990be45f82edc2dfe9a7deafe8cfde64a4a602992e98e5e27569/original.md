```
SAFTVREMie(solvents::Array{String,1}, 
    ions::Array{String,1}; 
    idealmodel::IdealModel = BasicIdeal,
    neutralmodel::EoSModel = SAFTVRMie,
    ionmodel::IonModel = MSABorn,
    RSPmodel::RSPModel = Schreckenberg,
    userlocations::Vector{String} = [],
    ideal_userlocations::Vector{String} = [],
    assoc_options::AssocOptions = AssocOptions(),
    verbose::Bool = false,
    reference_state = nothing)
```

## Description

This function is used to create an SAFT-VRE Mie model which is a combination of the SAFT-VR Mie, MSA and Born models.

## Input parameters

### SAFT-VR Mie Parameters

  * `Mw`: Single Parameter (`Float64`) - Molecular Weight `[g/mol]`
  * `segment`: Single Parameter (`Float64`) - Number of segments (no units)
  * `sigma`: Single Parameter (`Float64`) - Segment Diameter [`A°`]
  * `epsilon`: Single Parameter (`Float64`) - Reduced dispersion energy  `[K]`
  * `lambda_a`: Pair Parameter (`Float64`) - Atractive range parameter (no units)
  * `lambda_r`: Pair Parameter (`Float64`) - Repulsive range parameter (no units)
  * `k`: Pair Parameter (`Float64`) (optional) - Binary Interaction Paramater (no units)
  * `epsilon_assoc`: Association Parameter (`Float64`) - Reduced association energy `[K]`
  * `bondvol`: Association Parameter (`Float64`) - Association Volume `[m^3]`

### MSA Parameters

  * `sigma`: Single Parameter (`Float64`) - Diameter of closest approach `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

### Born Parameters

  * `sigma_born`: Single Parameter (`Float64`) - Born Diameter `[m]`
  * `charge`: Single Parameter (`Float64`) - Charge `[-]`

## Input models

  * `idealmodel`: Ideal Model
  * `neutralmodel`: Neutral EoS Model
  * `ionmodel`: Ion Model

## References

1. Eriksen, D.K., Lazarou, G., Galindo, A., Jackson, G., Adjiman, C.S., & Haslam, A.J. (2016). Development of intermolecular potential models for electrolyte solutions using an electrolyte SAFT-VR Mie equation of state. Molecular Physics, 114(18), 2724-2749.
