```
struct MatDeforElastOrtho{
    MR<:AbstractDeforModelRed,
    FT,
    MTAN<:Function,
    MUPD<:Function,
    MTHS<:Function,
} <: AbstractMatDeforLinearElastic
```

Linear orthotropic elasticity  material.
