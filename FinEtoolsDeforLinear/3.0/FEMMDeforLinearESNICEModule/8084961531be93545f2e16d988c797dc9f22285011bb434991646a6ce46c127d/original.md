```
mutable struct FEMMDeforLinearESNICEH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetH8},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearESNICE
```

FEMM type for Energy-sampling Stabilized Nodally Integrated Continuum Elements (ESNICE) based on the 8-node hexahedron.
