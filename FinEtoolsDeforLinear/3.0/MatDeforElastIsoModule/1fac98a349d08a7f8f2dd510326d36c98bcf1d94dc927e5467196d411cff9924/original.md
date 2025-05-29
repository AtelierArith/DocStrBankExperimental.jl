```
struct MatDeforElastIso{
    MR<:AbstractDeforModelRed,
    FT,
    MTAN<:Function,
    MUPD<:Function,
    MTHS<:Function,
} <: AbstractMatDeforLinearElastic
```

Linear isotropic elasticity  material.
