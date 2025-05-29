```
manifold_dimension(M::CenteredMatrices)
```

Return the manifold dimension of the [`CenteredMatrices`](@ref) `m`-by-`n` matrix `M` over the number system `𝔽`, i.e.

$$
\dim(\mathcal M) = (m*n - n) \dim_ℝ 𝔽,
$$

where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of `𝔽`.
