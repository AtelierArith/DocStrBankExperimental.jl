```
stiffness(
    self::FEMM,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{T},
) where {FEMM<:AbstractFEMMDeforLinearESNICE,A<:AbstractSysmatAssembler,GFT<:Number,T<:Number}
```

Compute and assemble  stiffness matrix.
