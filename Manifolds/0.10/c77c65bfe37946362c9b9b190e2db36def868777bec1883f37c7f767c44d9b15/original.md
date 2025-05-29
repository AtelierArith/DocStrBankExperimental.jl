```
manifold_dimension(M::GeneralizedGrassmann)
```

Return the dimension of the [`GeneralizedGrassmann(n,k,𝔽)`](@ref) manifold `M`, i.e.

$$
\dim \operatorname{Gr}(n,k,B) = k(n-k) \dim_ℝ 𝔽,
$$

where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of `𝔽`.
