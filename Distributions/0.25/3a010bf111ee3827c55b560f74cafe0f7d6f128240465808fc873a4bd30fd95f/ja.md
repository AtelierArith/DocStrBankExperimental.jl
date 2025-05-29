```
MatrixNormal(M, U, V)
```

```julia
M::AbstractMatrix  n x p 平均
U::AbstractPDMat   n x n 行の共分散
V::AbstractPDMat   p x p 列の共分散
```

[matrix normal distribution](https://en.wikipedia.org/wiki/Matrix_normal_distribution)は、多変量正規分布を$n\times p$の実行列$\mathbf{X}$に一般化します。もし$\mathbf{X}\sim \textrm{MN}_{n,p}(\mathbf{M}, \mathbf{U}, \mathbf{V})$であれば、その確率密度関数は次のようになります。

$$
f(\mathbf{X};\mathbf{M}, \mathbf{U}, \mathbf{V}) = \frac{\exp\left( -\frac{1}{2} \, \mathrm{tr}\left[ \mathbf{V}^{-1} (\mathbf{X} - \mathbf{M})^{\rm{T}} \mathbf{U}^{-1} (\mathbf{X} - \mathbf{M}) \right] \right)}{(2\pi)^{np/2} |\mathbf{V}|^{n/2} |\mathbf{U}|^{p/2}}.
$$

$$
\mathbf{X}\sim \textrm{MN}_{n,p}(\mathbf{M},\mathbf{U},\mathbf{V})
$$

は、$\text{vec}(\mathbf{X})\sim \textrm{N}(\text{vec}(\mathbf{M}),\mathbf{V}\otimes\mathbf{U})$である場合に限ります。
