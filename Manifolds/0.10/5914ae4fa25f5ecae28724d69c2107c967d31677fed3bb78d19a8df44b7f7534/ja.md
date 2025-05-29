```
log(N::MetricManifold{M,G}, p, q)
```

[`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` に [`AbstractMetric`](@extref `ManifoldsBase.AbstractMetric`) `G` を装備して、対数写像を計算します。

もしメトリックが [`IsDefaultMetric`](@ref) 特性または [`is_default_metric`](@ref) を使用してデフォルトメトリックとして宣言されている場合、このメソッドは `log(M,p,q)` にフォールバックします。そうでない場合は、その [`MetricManifold`](@ref)`{M,G}` 内で非デフォルトの `AbstractMetric` `G` メトリックの実装を提供する必要があります。
