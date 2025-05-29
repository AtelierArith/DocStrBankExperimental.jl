```
mutable struct FEMMDeforLinearIMH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinear
```

Type for mean-strain linear deformation FEMM based on eight-node hexahedral elements with incompatible modes.

Default number of incompatible modes is 12 (Simo formulation). Alternative is 9 incompatible modes (Wilson formulation).
