```
manifold_dimension(M::Stiefel)
```

Return the dimension of the [`Stiefel`](@ref) manifold `M`=$\operatorname{St}(n,k,𝔽)$. The dimension is given by

$$
\begin{aligned}
\dim \mathrm{St}(n, k, ℝ) &= nk - \frac{1}{2}k(k+1)\\
\dim \mathrm{St}(n, k, ℂ) &= 2nk - k^2\\
\dim \mathrm{St}(n, k, ℍ) &= 4nk - k(2k-1)
\end{aligned}
$$
