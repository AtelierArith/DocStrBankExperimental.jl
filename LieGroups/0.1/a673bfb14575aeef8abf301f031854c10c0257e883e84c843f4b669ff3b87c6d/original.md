```
log(G::HeisenbergGroup, g, h)
```

Compute the logarithmic map on the [`HeisenbergGroup`](@ref) group.

We denote two points $g, h$ from the Heisenberg by

$$
g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}
\qquad
h = \begin{pmatrix} 1 & \mathbf{d}^{\mathrm{T}} & f\\ \mathbf{0}_n & I_n & \mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

where $I_n$ is the $n×n$ unit matrix, $\mathbf{a}, \mathbf{b}, \mathbf{d}, \mathbf{e} ∈ ℝ^n$ are vectors of length $n$, $\mathbf{0}_n$ is the zero vector of length $n$, and $c,f ∈ ℝ$ are real numbers.

Then formula reads

$$
\log_g(h) = \begin{pmatrix} 0 & (\mathbf{d}-\mathbf{q})^{\mathrm{T}} & f - c + \mathbf{a}^{\mathrm{T}}\mathbf{b} - \mathbf{d}^{\mathrm{T}}\mathbf{e} - \frac{1}{2}(\mathbf{d}-\mathbf{a})^{\mathrm{T}}(\mathbf{e}-\mathbf{b})\\ \mathbf{0}_n & Z_n & \mathbf{e} - \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

where additionally $Z_n$ denotes the $n×n$ zero matrix.
