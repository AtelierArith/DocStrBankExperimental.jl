```
mutable struct FEMMDeforLinearMSH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearMS
```

八ノード六面体要素に基づく平均ひずみ線形変形FEMMの型。
