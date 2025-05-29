```
manifold_dimension(M::SymmetricMatrices{n,𝔽})
```

Return the dimension of the [`SymmetricMatrices`](@ref) matrix `M` over the number system `𝔽`, i.e.

$$
\begin{aligned}
\dim \mathrm{Sym}(n,ℝ) &= \frac{n(n+1)}{2},\\
\dim \mathrm{Sym}(n,ℂ) &= 2\frac{n(n+1)}{2} - n = n^2,
\end{aligned}
$$

where the last $-n$ is due to the zero imaginary part for Hermitian matrices
