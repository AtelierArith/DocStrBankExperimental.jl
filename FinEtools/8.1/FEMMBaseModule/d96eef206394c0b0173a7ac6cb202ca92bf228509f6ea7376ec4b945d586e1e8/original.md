```
innerproduct(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    afield::NodalField{T},
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T}
```

Compute the inner-product (Gram) matrix.
