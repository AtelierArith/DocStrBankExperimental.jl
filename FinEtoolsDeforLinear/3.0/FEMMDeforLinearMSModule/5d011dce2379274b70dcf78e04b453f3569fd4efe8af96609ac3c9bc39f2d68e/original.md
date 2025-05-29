```
mutable struct FEMMDeforLinearMST10{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetT10,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearMS
```

Type for mean-strain linear deformation FEMM based on 10-node tetrahedral elements.
