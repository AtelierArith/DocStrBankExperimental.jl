```
exp(G::HeisenbergGroup, g, X)
```

左不変計量を持つ[`HeisenbergGroup`](@ref) `G`上の指数写像。

`g`をヘisenberg群の点、$X$をリー代数のベクトルとします。これらは次の形をしています。

$$
g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}
\qquad
X = \begin{pmatrix} 0 & \mathbf{d}^{\mathrm{T}} & f\\ \mathbf{0}_n & Z_n & \mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

ここで、$I_n$は$n×n$の単位行列、$Z_n$は$n×n$の零行列、$\mathbf{a}, \mathbf{b}, \mathbf{d}, \mathbf{e} ∈ ℝ^n$は長さ$n$のベクトル、$\mathbf{0}_n$は長さ$n$の零ベクトル、$c,f ∈ ℝ$は実数です。

次に、式は次のようになります。

$$
\exp_g(X) =
\begin{pmatrix} 1 & (\mathbf{a}+\mathbf{d})^{\mathrm{T}} & c+f+\frac{1}{2}\mathbf{d}^{\mathrm{T}}\mathbf{e} + \mathbf{a}^{\mathrm{T}}\mathbf{e}\\ \mathbf{0}_n & I_n & \mathbf{b}+\mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}.
$$
