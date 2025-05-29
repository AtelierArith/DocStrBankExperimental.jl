```
manifold_dimension(M::Grassmann)
```

[`Grassmann`](@ref)`(n,k,𝔽)` 多様体 `M` の次元を返します。すなわち、

$$
\dim \operatorname{Gr}(n,k) = k(n-k) \dim_ℝ 𝔽,
$$

ここで $\dim_ℝ 𝔽$ は [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) の `𝔽` です。
