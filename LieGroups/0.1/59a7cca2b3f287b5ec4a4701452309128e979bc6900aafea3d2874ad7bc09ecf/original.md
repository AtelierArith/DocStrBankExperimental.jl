```
exp(G::HeisenbergGroup, g, X)
```

Exponential map on the [`HeisenbergGroup`](@ref) `G` with the left-invariant metric.

We denote by `g` a point on the Heisenberg group and by $X$ a vector from the Lie algebra. These are of the form

$$
g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}
\qquad
X = \begin{pmatrix} 0 & \mathbf{d}^{\mathrm{T}} & f\\ \mathbf{0}_n & Z_n & \mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

where $I_n$ is the $n×n$ unit matrix, $Z_n$ is the $n×n$ zero matrix, $\mathbf{a}, \mathbf{b}, \mathbf{d}, \mathbf{e} ∈ ℝ^n$ are vectors of length $n$, $\mathbf{0}_n$ is the zero vector of length $n$, and $c,f ∈ ℝ$ are real numbers.

Then the formula reads

$$
\exp_g(X) =
\begin{pmatrix} 1 & (\mathbf{a}+\mathbf{d})^{\mathrm{T}} & c+f+\frac{1}{2}\mathbf{d}^{\mathrm{T}}\mathbf{e} + \mathbf{a}^{\mathrm{T}}\mathbf{e}\\ \mathbf{0}_n & I_n & \mathbf{b}+\mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}.
$$
