```
剛性(
    self::FEMM,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {FEMM<:AbstractFEMMDeforLinearMS,A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

剛性行列を計算して組み立てます。
