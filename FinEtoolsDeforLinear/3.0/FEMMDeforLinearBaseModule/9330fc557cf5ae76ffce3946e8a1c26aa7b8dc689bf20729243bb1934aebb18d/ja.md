```
thermalstrainloads(
    self::AbstractFEMMDeforLinear,
    assembler::A,
    geom::NodalField{GFT},
    u::NodalField{UFT},
    dT::NodalField{TFT},
) where {A<:AbstractSysvecAssembler,GFT<:Number,UFT<:Number,TFT<:Number}
```

熱ひずみ荷重ベクトルを計算します。
