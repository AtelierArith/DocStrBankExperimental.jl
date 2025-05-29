```
log(G::HeisenbergGroup, g, h)
```

[`HeisenbergGroup`](@ref)群における対数写像を計算します。

我々は、Heisenbergからの2つの点$g, h$を次のように表します。

$$
g = \begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}
\qquad
h = \begin{pmatrix} 1 & \mathbf{d}^{\mathrm{T}} & f\\ \mathbf{0}_n & I_n & \mathbf{e}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

ここで、$I_n$は$n×n$単位行列、$\mathbf{a}, \mathbf{b}, \mathbf{d}, \mathbf{e} ∈ ℝ^n$は長さ$n$のベクトル、$\mathbf{0}_n$は長さ$n$のゼロベクトル、$c,f ∈ ℝ$は実数です。

次に、式は次のようになります。

$$
\log_g(h) = \begin{pmatrix} 0 & (\mathbf{d}-\mathbf{q})^{\mathrm{T}} & f - c + \mathbf{a}^{\mathrm{T}}\mathbf{b} - \mathbf{d}^{\mathrm{T}}\mathbf{e} - \frac{1}{2}(\mathbf{d}-\mathbf{a})^{\mathrm{T}}(\mathbf{e}-\mathbf{b})\\ \mathbf{0}_n & Z_n & \mathbf{e} - \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

ここで、$Z_n$は$n×n$のゼロ行列を示します。
