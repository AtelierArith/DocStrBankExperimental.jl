```
FEMMDeforLinearIMH8(
    mr::Type{MR},
    integdomain::ID,
    mcsys::CS,
    material::M,
) where {
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    CS<:CSys,
    M<:AbstractMatDeforLinearElastic,
}
```

Constructor. Default number of incompatible modes.
