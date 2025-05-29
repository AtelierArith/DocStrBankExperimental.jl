```
FEMMDeforLinearESNICET4(
    mr::Type{MR},
    integdomain::ID,
    mcsys::CS,
    material::M,
) where {
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S} where {S<:FESetT4},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
}
```

Constructor.
