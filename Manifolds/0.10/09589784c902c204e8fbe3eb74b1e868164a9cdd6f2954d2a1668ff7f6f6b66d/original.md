```
manifold_dimension(M::SphereSymmetricMatrices{<:Any,𝔽})
```

Return the manifold dimension of the [`SphereSymmetricMatrices`](@ref) `n`-by-`n` symmetric matrix `M` of unit Frobenius norm over the number system `𝔽`, i.e.

$$
\begin{aligned}
\dim(\mathcal{S}_{\text{sym}})(n,ℝ) &= \frac{n(n+1)}{2} - 1,\\
\dim(\mathcal{S}_{\text{sym}})(n,ℂ) &= 2\frac{n(n+1)}{2} - n -1.
\end{aligned}
$$
