```
mutable struct FEMMDeforLinearNICET4{
    MR <: AbstractDeforModelRed,
    S <: FESetT4,
    F <: Function,
    M <: AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinearNICE
```

4ノードテトラヘドロンに基づくノード統合連続体要素（NICE）のためのFEMMタイプ。
