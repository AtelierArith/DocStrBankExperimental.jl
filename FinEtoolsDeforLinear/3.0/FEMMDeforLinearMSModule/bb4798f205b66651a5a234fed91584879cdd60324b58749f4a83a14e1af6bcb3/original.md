```
mutable struct FEMMDeforLinearMSH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearMS
```

Type for mean-strain linear deformation FEMM based on eight-node hexahedral elements.
