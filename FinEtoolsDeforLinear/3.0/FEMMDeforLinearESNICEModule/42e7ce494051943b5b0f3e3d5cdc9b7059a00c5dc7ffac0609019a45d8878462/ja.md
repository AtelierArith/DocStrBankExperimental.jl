```
FEMMDeforLinearESNICET4(
    mr::Type{MR},
    integdomain::ID,
    material::M,
) where {
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetT4},
    M<:AbstractMatDeforLinearElastic,
}
```

コンストラクタ。
