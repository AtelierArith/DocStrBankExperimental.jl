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

吸収境界条件 (ABC) に関連するダンピング行列を計算します。

表面の隣にある無粘性流体の無限の広がりの効果を表す吸収境界条件 (ABC) に関連するダンピング行列を計算します。
