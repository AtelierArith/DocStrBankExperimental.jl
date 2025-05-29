```
manifold_dimension(M::Stiefel)
```

[`Stiefel`](@ref) 多様体 `M`=$\operatorname{St}(n,k,𝔽)$ の次元を返します。次元は次のように与えられます。

$$
\begin{aligned}
\dim \mathrm{St}(n, k, ℝ) &= nk - \frac{1}{2}k(k+1)\\
\dim \mathrm{St}(n, k, ℂ) &= 2nk - k^2\\
\dim \mathrm{St}(n, k, ℍ) &= 4nk - k(2k-1)
\end{aligned}
$$
