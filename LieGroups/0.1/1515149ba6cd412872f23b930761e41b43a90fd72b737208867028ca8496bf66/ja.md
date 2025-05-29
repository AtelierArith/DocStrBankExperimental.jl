```
SymplecticGroup{T}
```

実数シンプレクティック行列のマニフォールド [real symplectic matrices](@extref `Manifolds.SymplecticMatrices`) は、サイズ $2n×2n$ のもので、$n∈ℕ$ のいずれかに対して次のように与えられます。

$$
\mathrm{Sp}(2n, ℝ) = \bigl\{ p ∈ ℝ^{2n×2n}\ \big|\ p^\mathrm{T}J_{2n}p = J_{2n}\bigr \}
$$

ここで、$J_{2n} = \begin{pmatrix} 0_n & I_n\\ -I_n & 0_n\end{pmatrix}$ は [`SymplecticElement`](@extref `Manifolds.SymplecticElement`) を示します。

これにより、[`SymplecticGroup`](@ref) と [`MatrixMultiplicationGroupOperation`](@ref) が群演算として得られます。

対応するリー代数は、[`HamiltonianMatrices`](@extref `Manifolds.HamiltonianMatrices`) によって次のように与えられます。

$$
\mathfrak so(2n, ℝ) = \bigl\{ X ∈ ℝ^{2n×2n}\ \big|\ X^+ = -X\bigr \},
$$

ここで、$⋅^+$ は [`symplectic_inverse`](@extref `Manifolds.symplectic_inverse`) を示します。

詳細については [BendokatZimmermann:2021; Section 2](@cite) を参照してください。
