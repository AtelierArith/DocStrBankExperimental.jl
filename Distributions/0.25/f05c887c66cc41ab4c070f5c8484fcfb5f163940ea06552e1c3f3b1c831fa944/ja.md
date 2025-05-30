```
MatrixTDist(ν, M, Σ, Ω)
```

```julia
ν::Real            正の自由度
M::AbstractMatrix  n x p の位置
Σ::AbstractPDMat   n x n のスケール
Ω::AbstractPDMat   p x p のスケール
```

[行列 *t*-分布](https://en.wikipedia.org/wiki/Matrix_t-distribution) は多変量 *t*-分布を $n\times p$ の実行列 $\mathbf{X}$ に一般化します。もし $\mathbf{X}\sim \textrm{MT}_{n,p}(\nu,\mathbf{M},\boldsymbol{\Sigma}, \boldsymbol{\Omega})$ であれば、その確率密度関数は次のようになります。

$$
f(\mathbf{X} ; \nu,\mathbf{M},\boldsymbol{\Sigma}, \boldsymbol{\Omega}) =
c_0 \left|\mathbf{I}_n + \boldsymbol{\Sigma}^{-1}(\mathbf{X} - \mathbf{M})\boldsymbol{\Omega}^{-1}(\mathbf{X}-\mathbf{M})^{\rm{T}}\right|^{-\frac{\nu+n+p-1}{2}},
$$

ここで

$$
c_0=\frac{\Gamma_p\left(\frac{\nu+n+p-1}{2}\right)}{(\pi)^\frac{np}{2} \Gamma_p\left(\frac{\nu+p-1}{2}\right)} |\boldsymbol{\Omega}|^{-\frac{n}{2}} |\boldsymbol{\Sigma}|^{-\frac{p}{2}}.
$$

もし結合分布 $p(\mathbf{S},\mathbf{X})=p(\mathbf{S})p(\mathbf{X}|\mathbf{S})$ が次のように与えられるなら、

$$
\begin{aligned}
\mathbf{S}&\sim \textrm{IW}_n(\nu + n - 1, \boldsymbol{\Sigma})\\
\mathbf{X}|\mathbf{S}&\sim \textrm{MN}_{n,p}(\mathbf{M}, \mathbf{S}, \boldsymbol{\Omega}),
\end{aligned}
$$

その場合、$\mathbf{X}$ の周辺分布は $\textrm{MT}_{n,p}(\nu,\mathbf{M},\boldsymbol{\Sigma},\boldsymbol{\Omega})$ です。
