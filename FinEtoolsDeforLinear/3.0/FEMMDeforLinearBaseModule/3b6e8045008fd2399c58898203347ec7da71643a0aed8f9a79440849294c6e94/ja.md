```
mass(
    self::AbstractFEMMDeforLinear,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

一貫した質量行列を計算します

これは、抽象線形変形FEMMの一般的なルーチンです。
