```
inv(::SymplecticStiefel, A)
inv!(::SymplecticStiefel, q, p)
```

行列 $A ∈ ℝ^{2n×2k}$ のシンプレクティック逆行列 $A^+$ を計算します。行列

$$
A ∈ ℝ^{2n×2k},\quad
A =
\begin{bmatrix}
A_{1, 1} & A_{1, 2} \\
A_{2, 1} & A_{2, 2}
\end{bmatrix}, \quad A_{i, j} ∈ ℝ^{2n×2k}
$$

のシンプレクティック逆行列は次のように定義されます：

$$
A^{+} := J_{2k}^{\mathrm{T}} A^{\mathrm{T}} J_{2n},
$$

ここで $J_{2n} = \begin{bmatrix} 0_n & I_n \\ -I_n & 0_n \end{bmatrix}$ は [`SymplecticElement`](@ref) を示します。

行列 A のシンプレクティック逆行列は明示的に次のように表現できます：

$$
A^{+} =
  \begin{bmatrix}
    A_{2, 2}^{\mathrm{T}} & -A_{1, 2}^{\mathrm{T}} \\[1.2mm]
   -A_{2, 1}^{\mathrm{T}} &  A_{1, 1}^{\mathrm{T}}
  \end{bmatrix}.
$$
