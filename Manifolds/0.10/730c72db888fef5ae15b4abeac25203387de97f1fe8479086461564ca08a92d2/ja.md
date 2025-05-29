```
manifold_dimension(M::CenteredMatrices)
```

[`CenteredMatrices`](@ref) `m`-行`n`-列の行列 `M` の多様体次元を数体系 `𝔽` に対して返します。すなわち、

$$
\dim(\mathcal M) = (m*n - n) \dim_ℝ 𝔽,
$$

ここで $\dim_ℝ 𝔽$ は [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) の `𝔽` です。
