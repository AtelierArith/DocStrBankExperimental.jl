```
mutable struct FEMMDeforLinearNICET4{
    MR <: AbstractDeforModelRed,
    S <: FESetT4,
    F <: Function,
    M <: AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinearNICE
```

FEMM type for Nodally Integrated Continuum Elements (NICE) based on the 4-node tetrahedron.
