```
mass(
    self::AbstractFEMMDeforLinear,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

Compute the consistent mass matrix

This is a general routine for the abstract linear-deformation  FEMM.
