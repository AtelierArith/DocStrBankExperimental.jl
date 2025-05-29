```
manifold_dimension(M::SymmetricPositiveSemidefiniteFixedRank)
```

Return the dimension of the [`SymmetricPositiveSemidefiniteFixedRank`](@ref) matrix `M` over the number system `𝔽`, i.e.

$$
\begin{aligned}
\dim \operatorname{SPS}_{k,ℝ}(n) &= kn - \frac{k(k-1)}{2},\\
\dim \operatorname{SPS}_{k,ℂ}(n) &= 2kn - k^2,
\end{aligned}
$$

where the last $k^2$ is due to the zero imaginary part for Hermitian matrices diagonal
