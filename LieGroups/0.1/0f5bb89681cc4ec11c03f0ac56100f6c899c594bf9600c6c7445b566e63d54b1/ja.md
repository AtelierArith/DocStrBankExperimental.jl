```
inv(G::SpecialEuclideanGroup, g)
inv(G::SpecialEuclideanGroup, h, g)
```

$$
g ∈ \mathrm{SE}(n)
$$

の逆要素を [`SpecialEuclideanGroup`](@ref)`(n)` から計算します。

アフィン形式では、$g = \begin{pmatrix} r & t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}$ であり、ここで $\mathbf{0}_n ∈ ℝ^n$ はゼロを含むベクトルを示します。

逆は次のように表されます。

$$
g^{-1} = \begin{pmatrix} r^{\mathrm{T}} & -r^{\mathrm{T}}t\\ \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix}.
$$

この計算は `h` のインプレースで行うことができます。
