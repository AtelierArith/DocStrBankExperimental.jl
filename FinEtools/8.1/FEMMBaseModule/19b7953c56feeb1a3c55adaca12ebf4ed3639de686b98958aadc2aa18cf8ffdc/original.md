```
distribloads(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    P::NodalField{T},
    fi::ForceIntensity,
    m,
) where {FEMM<:AbstractFEMM, A<:AbstractSysvecAssembler, FT<:Number, T}
```

Compute distributed loads vector.

# Arguments

  * `fi`=force intensity object
  * `m`= manifold dimension, 0= vertex (point), 1= curve, 2= surface, 3= volume. For body loads `m` is set to 3, for tractions on the surface it is set to 2, and so on.

The actual work is done by `linform_dot()`.
