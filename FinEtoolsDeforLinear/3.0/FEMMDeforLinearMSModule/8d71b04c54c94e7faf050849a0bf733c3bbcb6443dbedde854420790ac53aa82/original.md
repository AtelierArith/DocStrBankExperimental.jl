```
FEMMDeforLinearMSH8(
    mr::Type{MR},
    integdomain::ID,
    material::M,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S} where {S<:FESetH8}, M<:AbstractMatDeforLinearElastic}
```

Constructor.
