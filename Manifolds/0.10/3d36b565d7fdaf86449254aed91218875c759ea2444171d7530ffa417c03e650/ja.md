```
inner(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,LogCholeskyMetric}, p, X, Y)
```

点 `p` の接空間における二つの行列 `X` と `Y` の内積を、[`SymmetricPositiveDefinite`](@ref) 多様体 `M` 上の [`MetricManifold`](@ref) として、[`LogCholeskyMetric`](@ref) を用いて計算します。式は次のようになります。

$$
    g_p(X,Y) = ⟨a_z(X),a_z(Y)⟩_z,
$$

ここで、$⟨⋅,⋅⟩_x$ は [`CholeskySpace`](@ref) 上の内積を示し、$z$ は $p$ のコレスキー因子、$a_z(W) = z (z^{-1}Wz^{-\mathrm{T}})_{\frac{1}{2}}$ であり、$(⋅)_\frac{1}{2}$ は対角成分が $\frac{1}{2}$ 倍された下三角行列を示します。
