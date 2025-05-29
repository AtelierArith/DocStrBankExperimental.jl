```
manifold_dimension(M::PowerManifold)
```

[`PowerManifold`](@ref) `M` の多様体次元を返します $=\mathcal N = (\mathcal M)^{n_1,…,n_d}$。すなわち、$n=(n_1,…,n_d)$ はパワー多様体の配列サイズであり、$d_{\mathcal M}$ は基底多様体 $\mathcal M$ の次元です。この多様体の次元は次のようになります。

$$
\dim(\mathcal N) = \dim(\mathcal M)\prod_{i=1}^d n_i = n_1n_2⋅…⋅ n_d \dim(\mathcal M).
$$
