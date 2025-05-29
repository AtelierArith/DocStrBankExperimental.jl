```
inspectintegpoints(self::FEMM,
    geom::NodalField{GFT},
    u::NodalField{FT},
    dT::NodalField{FT},
    felist::AbstractVector{IT},
    inspector::F,
    idat,
    quantity = :Cauchy;
    context...,) where {FEMM<:AbstractFEMM, GFT, IT, FT, F <: Function}
```

Inspect integration points.
