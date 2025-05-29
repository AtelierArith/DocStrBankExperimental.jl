```
innerproduct(
    self::FEMM,
    assembler::A,
    geom::NodalField{FT},
    afield::NodalField{T},
) where {FEMM<:AbstractFEMM, A<:AbstractSysmatAssembler, FT, T}
```

内積（グラム）行列を計算します。
