```
SymmetricBZ(A, B, lims::AbstractIteratedLimits, syms; atol=sqrt(eps()))
```

対称性 `syms` によって縮小されたブリルアンゾーンを表すデータ型で、反復積分限界 `lims` が含まれ、両方とも格子基底であると仮定されます（フーリエ級数がそうであるため）。`A` と `B` は、実基底ベクトルと逆基底ベクトルを列に持つ同じサイズの正方行列である必要があります。

!!! note "慣例"
    この型は、すべての積分限界データが分数座標の逆格子基底にあると仮定しており、FBZは単に頂点 (0,…,0) と (1,…,1) によって張られるハイパーキューブです。必要に応じて、これらの量を慣例に合わせるために `A` または `B` を使用してください。


`lims` は [IteratedIntegration.jl](https://github.com/lxvm/IteratedIntegration.jl) と互換性のある限界である必要があります。`syms` は [AutoSymPTR.jl](https://github.com/lxvm/AutoSymPTR.jl) と互換性のある点群対称性の反復可能なコレクションである必要があります。
