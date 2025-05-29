```
log(G::HeisenbergGroup, g)
log!(G::HeisenbergGroup, X, g)
```

[`HeisenbergGroup`](@ref) `G` のリー群対数を計算します。

$$
g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}
$$

はヘisenberg群のリー代数からのもので、ここで $\mathbf{a}, \mathbf{b} ∈ ℝ^n$ は長さ $n$ のベクトル、$\mathbf{0}_n$ は長さ $n$ のゼロベクトル、$c ∈ ℝ$、$I_n$ は $n×n$ 単位行列です。

次に、

$$
\log_{\mathcal G}(g) =
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c - \frac{1}{2}\mathbf{a}^{\mathrm{T}}\mathbf{b}\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

ここで $Z_n$ は $n×n$ のゼロ行列を示します。

これはリー代数ベクトル `X` のインプレースで計算できます。
