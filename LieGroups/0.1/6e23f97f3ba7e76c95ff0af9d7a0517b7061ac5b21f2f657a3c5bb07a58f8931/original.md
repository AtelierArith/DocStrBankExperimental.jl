```
exp(G::HeisenbergGroup, X)
exp!(G::HeisenbergGroup, g, X)
```

Compute the Lie group exponential for the [`HeisenbergGroup`](@ref) `G` of the vector `X`.

For $X = \begin{pmatrix} 0 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix}$ from the Lie algebra of the Heisenberg group, where $\mathbf{a}, \mathbf{b} ∈ ℝ^n$ vectors of length $n$, $\mathbf{0}_n$ is the zero vector of length $n$, $c ∈ ℝ$, and $Z_n$ denotes the $n×n$ zero matrix.

Then the

$$
\exp_{\mathcal G}(X) =
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c + \frac{1}{2}\mathbf{a}^{\mathrm{T}}\mathbf{b}\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

where $I_n$ is the $n×n$ unit matrix.

This can be computed in-place of the Lie group element `g`.
