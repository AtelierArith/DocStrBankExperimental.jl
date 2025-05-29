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

Constructor of linear deformation finite element modeling machine.
