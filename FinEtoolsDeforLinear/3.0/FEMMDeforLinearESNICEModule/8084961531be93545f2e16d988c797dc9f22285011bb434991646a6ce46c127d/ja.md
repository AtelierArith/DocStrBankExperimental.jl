```
mutable struct FEMMDeforLinearESNICEH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetH8},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
    MS<:MatDeforElastIso,
} <: AbstractFEMMDeforLinearESNICE
```

エネルギーサンプリング安定化ノード統合連続要素（ESNICE）のためのFEMMタイプで、8ノードのヘキサヘドロンに基づいています。
