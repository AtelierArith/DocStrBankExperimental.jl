```
mutable struct FEMMDeforLinear{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain,
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinear
```

Type for linear deformation finite element modeling machine.
