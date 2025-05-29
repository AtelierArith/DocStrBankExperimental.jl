```
std(M, x, m=mean(M, x); corrected=true, kwargs...)
std(M, x, w::AbstractWeights, m=mean(M, x, w); corrected=false, kwargs...)
```

は、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)  `M` 上の `n` データポイントの `Vector` `x` のオプションで重み付けされた標準偏差を計算します。すなわち、

$$
\sqrt{\frac{1}{c} \sum_{i=1}^n w_i d_{\mathcal M}^2 (x_i,m)},
$$

ここで `c` は補正項です。詳細は [Statistics.std](https://juliastats.org/StatsBase.jl/stable/scalarstats/#Statistics.std) を参照してください。`x` の平均は `m` として指定でき、補正された分散は `corrected=true` に設定することで有効にできます。
