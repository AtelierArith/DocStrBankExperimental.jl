```
dampingABC(
    self::FEMMDeforSurfaceDamping,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    impedance::FT,
    surfacenormal::SurfaceNormal,
) where {A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number,FT<:Number}
```

Compute the damping matrix associated with absorbing boundary conditions (ABC).

Compute the damping matrix associated with absorbing boundary conditions (ABC) representation of the effect of infinite extent of inviscid fluid next to the surface.
