```
log(G::HeisenbergGroup, g)
log!(G::HeisenbergGroup, X, g)
```

Compute the Lie group logarithm for the [`HeisenbergGroup`](@ref) `G`.

For $g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}$ from the Lie algebra of the Heisenberg group, where $\mathbf{a}, \mathbf{b} ∈ ℝ^n$ vectors of length $n$, $\mathbf{0}_n$ is the zero vector of length $n$, $c ∈ ℝ$, and $I_n$ is the $n×n$ unit matrix.

Then the

$$
\log_{\mathcal G}(g) =
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c - \frac{1}{2}\mathbf{a}^{\mathrm{T}}\mathbf{b}\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

where $Z_n$ denotes the $n×n$ zero matrix.

This can be computed in-place of the Lie algebra vector `X`.
