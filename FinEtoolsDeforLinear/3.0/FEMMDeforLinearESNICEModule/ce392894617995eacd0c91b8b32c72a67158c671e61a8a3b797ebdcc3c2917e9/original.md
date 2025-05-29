```
mutable struct FEMMDeforLinearESNICET4{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetT4},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearESNICE
```

FEMM type for Energy-sampling Stabilized Nodally Integrated Continuum Elements (ESNICE) based on the 4-node tetrahedron.
