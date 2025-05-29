```
inverse_local_metric(M::AbstractcManifold{𝔽}, p, B::AbstractBasis)
```

点 `p` における接空間の逆計量（コメトリック）テンソルのローカル行列表現を、[`AbstractManifold`](https://juliamanifolds.github.io/Manifolds.jl/latest/interface.html#ManifoldsBase.AbstractManifold) `M` に対して、[`AbstractBasis`](@extref `ManifoldsBase.AbstractBasis`) 基底 `B` を用いて返します。

計量テンソル（[`local_metric`](@ref) を参照）は通常 $G = (g_{ij}) ∈ 𝔽^{d×d}$ で表され、ここで $d$ は多様体の次元です。

逆ローカル計量は $G^{-1} = g^{ij}$ で表されます。 ```
