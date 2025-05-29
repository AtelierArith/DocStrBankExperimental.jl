```
FEMMDeforLinearIMH8(
    mr::Type{MR},
    integdomain::ID,
    material::M,
) where {
    MR<:AbstractDeforModelRed,
    ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function},
    M<:AbstractMatDeforLinearElastic,
}
```

Constructor. Default number of incompatible modes.
