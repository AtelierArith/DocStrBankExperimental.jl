```
manifold_dimension(M::GeneralizedStiefel)
```

Return the dimension of the [`GeneralizedStiefel`](@ref) manifold `M`=$\operatorname{St}(n,k,B,𝔽)$. The dimension is given by

$$
\begin{aligned}
\dim \mathrm{St}(n, k, B, ℝ) &= nk - \frac{1}{2}k(k+1) \\
\dim \mathrm{St}(n, k, B, ℂ) &= 2nk - k^2\\
\dim \mathrm{St}(n, k, B, ℍ) &= 4nk - k(2k-1)
\end{aligned}
$$
