```
manifold_dimension(M::SphereSymmetricMatrices{<:Any,𝔽})
```

単位フロベニウスノルムを持つ [`SphereSymmetricMatrices`](@ref) の `n`-by-`n` 対称行列 `M` の多様体次元を返します。すなわち、

$$
\begin{aligned}
\dim(\mathcal{S}_{\text{sym}})(n,ℝ) &= \frac{n(n+1)}{2} - 1,\\
\dim(\mathcal{S}_{\text{sym}})(n,ℂ) &= 2\frac{n(n+1)}{2} - n -1.
\end{aligned}
$$
