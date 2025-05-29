```
inv(::SymplecticStiefel, A)
inv!(::SymplecticStiefel, q, p)
```

Compute the symplectic inverse $A^+$ of matrix $A ∈ ℝ^{2n×2k}$. Given a matrix

$$
A ∈ ℝ^{2n×2k},\quad
A =
\begin{bmatrix}
A_{1, 1} & A_{1, 2} \\
A_{2, 1} & A_{2, 2}
\end{bmatrix}, \quad A_{i, j} ∈ ℝ^{2n×2k}
$$

the symplectic inverse is defined as:

$$
A^{+} := J_{2k}^{\mathrm{T}} A^{\mathrm{T}} J_{2n},
$$

where $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ denotes the [`SymplecticElement`](@ref).

The symplectic inverse of a matrix A can be expressed explicitly as:

$$
A^{+} =
  \begin{bmatrix}
    A_{2, 2}^{\mathrm{T}} & -A_{1, 2}^{\mathrm{T}} \\[1.2mm]
   -A_{2, 1}^{\mathrm{T}} &  A_{1, 1}^{\mathrm{T}}
  \end{bmatrix}.
$$
