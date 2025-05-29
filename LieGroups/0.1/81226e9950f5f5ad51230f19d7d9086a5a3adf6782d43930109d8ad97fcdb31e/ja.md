```
HeisenbergGroup{T}
```

`HeisenbergGroup(n)` は $(n+2)×(n+2)$ 行列の群であり、[BinzPods:2008](@cite) または [Heisenberg group](https://en.wikipedia.org/wiki/Heisenberg_group) を参照してください。ここで `T` は行列のエントリの `eltype` を指定します。

$$
\begin{pmatrix} 1 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & I_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 1\end{pmatrix},
$$

ここで $I_n$ は $n×n$ 単位行列、$\mathbf{a}, \mathbf{b} ∈ ℝ^n$ は長さ $n$ のベクトル、$\mathbf{0}_n$ は長さ $n$ のゼロベクトル、$c ∈ ℝ$ は実数です。群の演算は行列の乗算です。

リー代数は次の要素から構成されます。

$$
\begin{pmatrix} 0 & \mathbf{a}^{\mathrm{T}} & c\\ \mathbf{0}_n & Z_n & \mathbf{b}\\ 0 & \mathbf{0}_n^{\mathrm{T}} & 0\end{pmatrix},
$$

ここで $Z_n$ は $n×n$ ゼロ行列を示します。
