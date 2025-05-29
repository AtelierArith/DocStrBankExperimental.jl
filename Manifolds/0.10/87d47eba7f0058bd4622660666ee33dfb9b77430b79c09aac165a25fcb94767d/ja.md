```
manifold_dimension(M::GeneralizedStiefel)
```

[`GeneralizedStiefel`](@ref) 多様体 `M`=$\operatorname{St}(n,k,B,𝔽)$ の次元を返します。次元は次のように与えられます。

$$
\begin{aligned}
\dim \mathrm{St}(n, k, B, ℝ) &= nk - \frac{1}{2}k(k+1) \\
\dim \mathrm{St}(n, k, B, ℂ) &= 2nk - k^2\\
\dim \mathrm{St}(n, k, B, ℍ) &= 4nk - k(2k-1)
\end{aligned}
$$
