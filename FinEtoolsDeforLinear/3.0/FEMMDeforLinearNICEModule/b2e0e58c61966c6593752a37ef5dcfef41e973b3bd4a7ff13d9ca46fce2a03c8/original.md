```
stiffness(self::AbstractFEMMDeforLinearNICE,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT}) where {A <: AbstractSysmatAssembler, GFT <: Number, UFT <: Number}
```

Compute and assemble  stiffness matrix.
