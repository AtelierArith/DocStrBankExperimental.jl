```
mutable struct FEMMDeforLinear{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain,
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinear
```

線形変形有限要素モデリングマシンの型。
