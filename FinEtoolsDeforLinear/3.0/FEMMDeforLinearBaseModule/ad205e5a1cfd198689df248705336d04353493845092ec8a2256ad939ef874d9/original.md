```
stiffness(
    self::FEMM,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {FEMM<:AbstractFEMMDeforLinear,A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

Compute and assemble stiffness matrix.

!!! note "Only for homogeneous materials"
    The material stiffness matrix is assumed to be the same at all the points of the domain (homogeneous material).

