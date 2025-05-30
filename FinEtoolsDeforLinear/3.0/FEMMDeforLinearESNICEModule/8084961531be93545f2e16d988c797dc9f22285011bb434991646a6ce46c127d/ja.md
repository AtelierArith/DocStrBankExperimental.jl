```
mutable struct FEMMDeforLinearESNICEH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetH8},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearESNICE
```

8ノード六面体に基づくエネルギーサンプリング安定化ノード統合連続体要素（ESNICE）のためのFEMMタイプ。
