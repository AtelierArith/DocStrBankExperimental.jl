```
HeisenbergGroup{T}
```

The `HeisenbergGroup(n)` is the group of $(n+2)×(n+2)$ matrices, see also [BinzPods:2008](@cite) or [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) where `T` specifies the `eltype` of the matrix entries.

$$
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

where $I_n$ is the $n×n$ unit matrix, $\mathbf{a}, \mathbf{b} ∈ ℝ^n$ are vectors of length $n$, $\mathbf{0}_n$ is the zero vector of length $n$, and $c ∈ ℝ$ is a real number. The group operation is matrix multiplication.

The Lie algebra consists of the elements

$$
\begin{pmatrix} 0 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

where additionally $Z_n$ denotes the $n×n$ zero matrix.
