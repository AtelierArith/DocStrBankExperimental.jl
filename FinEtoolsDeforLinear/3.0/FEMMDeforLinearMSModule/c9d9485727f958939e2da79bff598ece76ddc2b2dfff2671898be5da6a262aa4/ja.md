```
FEMMDeforLinearMSH8(
    mr::Type{MR},
    integdomain::ID,
    mcsys::CS,
    material::M,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S} where {S<:FESetH8}, CS<:CSys, M<:AbstractMatDeforLinearElastic}
```

コンストラクタ。
