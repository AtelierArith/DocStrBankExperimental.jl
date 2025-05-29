```
surfacenormalspringstiffness(
    self::FEMMDeforWinkler,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    springconstant::UFT,
    surfacenormal::SurfaceNormal,
) where {A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

Compute the stiffness matrix of surface normal spring.

Rationale: consider continuously distributed springs between the surface of the solid body and the 'ground', in the direction normal to the surface. If the spring coefficient becomes large, we have an approximate method of enforcing the normal displacement to the surface.
