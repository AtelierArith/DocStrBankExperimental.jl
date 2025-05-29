```
FEMMDeforLinearMST10(
    mr::Type{MR},
    integdomain::ID,
    material::M,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S} where {S<:FESetT10}, M<:AbstractMatDeforLinearElastic}
```

コンストラクタ。
