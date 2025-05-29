```
exp(G, e, X)
exp!(G, e, g, X)
```

[`OrthogonalGroup`](@ref) $\mathrm{O}(4)$ または [`SpecialOrthogonalGroup`](@ref) $\mathrm{SO}(4)$ 上でのリー群指数関数を計算します。ここで `e` は [`Identity`](@ref)`{MatrixMultiplicationGroupOperation}` であり、`G` はディスパッチのために [`TypeParameter`](@extref `ManifoldsBase.TypeParameter`) を使用します。

$$
3×3
$$

の場合と同様に、[GallierXu:2002](@cite)、[AndricaRohan:2013](@cite) から適応された効率的な計算が提供されており、いくつかの数値的安定化が行われています。
