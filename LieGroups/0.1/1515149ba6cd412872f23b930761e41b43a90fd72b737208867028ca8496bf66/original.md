```
SymplecticGroup{T}
```

The manifold of [real symplectic matrices](@extref `Manifolds.SymplecticMatrices`), of size $2n×2n$ for some $n∈ℕ$ is given by

$$
\mathrm{Sp}(2n, ℝ) = \bigl\{ p ∈ ℝ^{2n×2n}\ \big|\ p^\mathrm{T}J_{2n}p = J_{2n}\bigr \}
$$

where $J_{2n} = \begin{pmatrix} 0_n & I_n\\ -I_n & 0_n\end{pmatrix}$ denotes the [`SymplecticElement`](@extref `Manifolds.SymplecticElement`).

This yields the [`SymplecticGroup`](@ref) together with the [`MatrixMultiplicationGroupOperation`](@ref) as the group operation.

The corresponding Lie algebra is given by the [`HamiltonianMatrices`](@extref `Manifolds.HamiltonianMatrices`)

$$
\mathfrak so(2n, ℝ) = \bigl\{ X ∈ ℝ^{2n×2n}\ \big|\ X^+ = -X\bigr \},
$$

where $⋅^+$ denotes the [`symplectic_inverse`](@extref `Manifolds.symplectic_inverse`).

See [BendokatZimmermann:2021; Section 2](@cite) for more information.
