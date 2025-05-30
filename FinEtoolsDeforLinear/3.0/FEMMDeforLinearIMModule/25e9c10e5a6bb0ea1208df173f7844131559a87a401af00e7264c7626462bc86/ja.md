```
mutable struct FEMMDeforLinearIMH8{
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinear
```

8ノード六面体要素を用いた不適合モードに基づく平均ひずみ線形変形FEMMの型。

不適合モードのデフォルト数は12（シモの定式化）です。代替として9つの不適合モード（ウィルソンの定式化）があります。
