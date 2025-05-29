```
mutable struct FEMMDeforLinearNICEH8{
    MR <: AbstractDeforModelRed,
    S <: FESetH8,
    F <: Function,
    M <: AbstractMatDeforLinearElastic,
} <: AbstractFEMMDeforLinearNICE
```

八ノード六面体に基づくノード統合連続体要素（NICE）のためのFEMMタイプ。
