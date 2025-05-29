```
manifold_dimension(M::Grassmann)
```

Return the dimension of the [`Grassmann`](@ref)`(n,k,𝔽)` manifold `M`, i.e.

$$
\dim \operatorname{Gr}(n,k) = k(n-k) \dim_ℝ 𝔽,
$$

where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of `𝔽`.
