```
manifold_dimension(M::SkewHermitianMatrices)
```

行列 `M` の次元を返します。これは [`SkewHermitianMatrices`](@ref) 行列で、数体系 `𝔽` 上の次元です。すなわち、

$$
\dim \mathrm{SkewHerm}(n,ℝ) = \frac{n(n+1)}{2} \dim_ℝ 𝔽 - n,
$$

ここで $\dim_ℝ 𝔽$ は [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) です。最初の項は行列の上三角要素のみが一意であることに対応し、2 番目の項は対角の実部がゼロであるという制約に対応します。
