```
log(M::MetricManifold{ℝ,<:SymmetricPositiveDefinite,LogCholeskyMetric}, p, q)
```

[`SymmetricPositiveDefinite`](@ref) `M` における [`LogCholeskyMetric`](@ref) に関して、点 `p` から点 `q` への対数写像を計算します。この式は [`CholeskySpace`](@ref) から適応できます。

$$
\log_p q = xW^{\mathrm{T}} + Wx^{\mathrm{T}},
$$

ここで、$x$ は $p$ のコレスキー因子であり、$W=\log_x y$ で、$y$ は $q$ のコレスキー因子であり、前述の対数写像は [`CholeskySpace`](@ref) におけるものです。
