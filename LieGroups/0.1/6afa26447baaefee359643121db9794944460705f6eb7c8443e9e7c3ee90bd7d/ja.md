```
log(G, g)
log!(G, X, g)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(4)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(4)$ 上でのリー群対数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

実装はロドリゲスの類似式の一般化されたバリアントに基づいています。詳細については [GallierXu:2002; Section 3](@cite) を参照してください。

この結果は `X` のインプレースで計算できます。

対数写像は、単位元の周りでのみ一意に決定されることに注意してください。
