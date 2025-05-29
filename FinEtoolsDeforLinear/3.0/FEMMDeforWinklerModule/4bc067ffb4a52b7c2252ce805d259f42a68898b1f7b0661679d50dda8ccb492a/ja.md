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

表面法線スプリングの剛性行列を計算します。

理由：固体の表面と「地面」の間に連続的に分布したスプリングを考慮し、表面に対して法線方向に配置します。スプリング係数が大きくなると、表面への法線変位を強制する近似的な方法が得られます。
