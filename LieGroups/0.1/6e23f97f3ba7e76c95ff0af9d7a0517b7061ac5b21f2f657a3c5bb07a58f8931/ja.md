```
exp(G::HeisenbergGroup, X)
exp!(G::HeisenbergGroup, g, X)
```

ベクトル `X` の [`HeisenbergGroup`](@ref) `G` に対するリー群指数を計算します。

リー代数のヘイゼンベルグ群からの $X = \begin{pmatrix} 0 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix}$ で、ここで $\mathbf{a}, \mathbf{b} ∈ ℝ^n$ は長さ $n$ のベクトル、$\mathbf{0}_n$ は長さ $n$ のゼロベクトル、$c ∈ ℝ$、$Z_n$ は $n×n$ のゼロ行列を示します。

次に、

$$
\exp_{\mathcal G}(X) =
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c + \frac{1}{2}\mathbf{a}^{\mathrm{T}}\mathbf{b}\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

ここで $I_n$ は $n×n$ の単位行列です。

これはリー群要素 `g` のインプレースで計算できます。 ```
