```
FEMMDeforLinearMST10(
    mr::Type{MR},
    integdomain::ID,
    mcsys::CS,
    material::M,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S} where {S<:FESetT10}, CS<:CSys, M<:AbstractMatDeforLinearElastic}
```

コンストラクタ。
