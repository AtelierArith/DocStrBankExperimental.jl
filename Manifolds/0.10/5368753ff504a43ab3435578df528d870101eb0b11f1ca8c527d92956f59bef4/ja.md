```
manifold_dimension(M::SymmetricMatrices{n,𝔽})
```

行列 `M` の次元を返します [`SymmetricMatrices`](@ref) 数体系 `𝔽` において、すなわち

$$
\begin{aligned}
\dim \mathrm{Sym}(n,ℝ) &= \frac{n(n+1)}{2},\\
\dim \mathrm{Sym}(n,ℂ) &= 2\frac{n(n+1)}{2} - n = n^2,
\end{aligned}
$$

最後の $-n$ はエルミート行列のゼロ虚部によるものです。
