```
mutable struct FEMMDeforLinearNICEH8{
    MR <: AbstractDeforModelRed,
    S <: FESetH8,
    F <: Function,
    M <: AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinearNICE
```

FEMM type for Nodally Integrated Continuum Elements (NICE) based on the eight-node hexahedron.
