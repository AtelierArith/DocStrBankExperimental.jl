```
mutable struct FEMMDeforLinearIMH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinear
```

8ノード六面体要素を用いた平均ひずみ線形変形FEMMの型で、互換性のないモードを持っています。

デフォルトの互換性のないモードの数は12（シモの定式化）です。代替として9の互換性のないモード（ウィルソンの定式化）があります。
