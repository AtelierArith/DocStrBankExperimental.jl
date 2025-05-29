```
manifold_dimension(M::SkewHermitianMatrices)
```

Return the dimension of the [`SkewHermitianMatrices`](@ref) matrix `M` over the number system `𝔽`, i.e.

$$
\dim \mathrm{SkewHerm}(n,ℝ) = \frac{n(n+1)}{2} \dim_ℝ 𝔽 - n,
$$

where $\dim_ℝ 𝔽$ is the [`real_dimension`](@extref `ManifoldsBase.real_dimension-Tuple{ManifoldsBase.AbstractNumbers}`) of $𝔽$. The first term corresponds to only the upper triangular elements of the matrix being unique, and the second term corresponds to the constraint that the real part of the diagonal be zero.
