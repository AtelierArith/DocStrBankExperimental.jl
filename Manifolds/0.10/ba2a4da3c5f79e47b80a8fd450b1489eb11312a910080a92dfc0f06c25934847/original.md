```
manifold_dimension(M::FixedRankMatrices)
```

Return the manifold dimension for the `𝔽`-valued [`FixedRankMatrices`](@ref) `M` of dimension `m`x`n` of rank `k`, namely

$$
\dim(\mathcal M) = k(m + n - k) \dim_ℝ 𝔽,
$$

where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of `𝔽`.
