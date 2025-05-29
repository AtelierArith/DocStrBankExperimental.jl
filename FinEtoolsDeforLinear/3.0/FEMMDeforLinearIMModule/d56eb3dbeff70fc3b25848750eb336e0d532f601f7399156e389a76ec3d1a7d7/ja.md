```
剛性(
    self::FEMMDeforLinearIMH8,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
) where {A<:AbstractSysmatAssembler,GFT<:Number,UFT<:Number}
```

剛性行列を計算して組み立てます。
