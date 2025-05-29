```
mutable struct FEMMDeforLinearESNICET4{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetT4},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearESNICE
```

エネルギーサンプリング安定化ノード統合連続要素（ESNICE）のためのFEMMタイプで、4ノードの四面体に基づいています。
