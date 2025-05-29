```
inner(N::MetricManifold{M,G}, p, X, Y)
```

点 `p` における接空間から `X` と `Y` の内積を計算します。これは [`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` のもので、[`AbstractMetric`](@extref `ManifoldsBase.AbstractMetric`) `G` を使用します。もし `M` が `G` をその [`IsDefaultMetric`](@ref) 特性として持っている場合、これは `inner(M, p, X, Y)` を使用して行われます。そうでない場合は、[`local_metric`](@ref)`(M, p)` が次のように使用されます。

$$
g_p(X, Y) = ⟨X, G_p Y⟩,
$$

ここで $G_p$ は `AbstractMetric` `G` の局所行列表現です。
