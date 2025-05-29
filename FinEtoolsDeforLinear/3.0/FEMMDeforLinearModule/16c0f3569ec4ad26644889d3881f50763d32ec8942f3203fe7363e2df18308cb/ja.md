```
FEMMDeforLinear(
    mr::Type{MR},
    integdomain::IntegDomain{S,F},
    material::M,
) where {
    MR<:AbstractDeforModelRed,
    S<:AbstractFESet,
    F<:Function,
    M<:AbstractMatDeforLinearElastic,
}
```

線形変形有限要素モデリングマシンのコンストラクタ。
