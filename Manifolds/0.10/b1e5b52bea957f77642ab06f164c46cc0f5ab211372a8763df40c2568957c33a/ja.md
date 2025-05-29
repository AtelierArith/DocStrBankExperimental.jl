```
local_metric(M::AbstractManifold{𝔽}, p, B::AbstractBasis)
```

点 `p` における計量テンソル $g$ の局所行列表現を、[`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) `B` に関して、[`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` 上で返します。$d$ を多様体の次元、$b_1,\ldots,b_d$ を基底ベクトルとします。すると、局所行列表現は行列 $G\in 𝔽^{n×n}$ であり、その要素は $g_{ij} = g_p(b_i,b_j), i,j\in\{1,…,d\}$ によって与えられます。

これにより、2つの接ベクトル (アインシュタインの総和規約を使用して) $X = X^ib_i, Y=Y^ib_i \in T_p\mathcal M$ に対して、$g_p(X, Y) = g_{ij} X^i Y^j$ という性質が得られます。
