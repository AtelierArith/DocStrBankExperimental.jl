```
FEMMDeforLinearIMH8(
    mr::Type{MR},
    integdomain::ID,
    material::M,
    nmodes::Int64,
) where {MR<:AbstractDeforModelRed, ID<:IntegDomain{S,F} where {S<:FESetH8,F<:Function}, M<:AbstractMatDeforLinearElastic}
```

Constructor, with optional configuration of the number of incompatible modes.
