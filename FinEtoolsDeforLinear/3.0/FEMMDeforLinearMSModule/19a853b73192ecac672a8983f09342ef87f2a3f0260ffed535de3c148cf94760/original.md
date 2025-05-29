```
stiffness(
    self::FEMM,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {FEMM<:AbstractFEMMDeforLinearMS,A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

Compute and assemble  stiffness matrix.
