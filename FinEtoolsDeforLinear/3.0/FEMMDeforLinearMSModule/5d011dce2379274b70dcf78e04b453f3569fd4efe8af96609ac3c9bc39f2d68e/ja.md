```
mutable struct FEMMDeforLinearMST10{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetT10,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearMS
```

10ノード四面体要素に基づく平均ひずみ線形変形FEMMの型。
