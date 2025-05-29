```
MatrixFDist(n1, n2, B)
```

```julia
n1::Real          自由度 (p - 1 より大きい)
n2::Real          自由度 (p - 1 より大きい)
B::AbstractPDMat  p x p スケール
```

[行列 *F*-分布](https://projecteuclid.org/euclid.ba/1515747744)（時々行列ベータタイプ II 分布と呼ばれる）は、*F*-分布を $p\times p$ の実数、正定値行列 $\boldsymbol{\Sigma}$ に一般化します。もし $\boldsymbol{\Sigma}\sim \textrm{MF}_{p}(n_1/2,n_2/2,\mathbf{B})$ であれば、その確率密度関数は次のようになります。

$$
f(\boldsymbol{\Sigma} ; n_1,n_2,\mathbf{B}) =
\frac{\Gamma_p(\frac{n_1+n_2}{2})}{\Gamma_p(\frac{n_1}{2})\Gamma_p(\frac{n_2}{2})}
|\mathbf{B}|^{n_2/2}|\boldsymbol{\Sigma}|^{(n_1-p-1)/2}|\mathbf{B}+\boldsymbol{\Sigma}|^{-(n_1+n_2)/2}.
$$

もし結合分布 $p(\boldsymbol{\Psi},\boldsymbol{\Sigma})=p(\boldsymbol{\Psi})p(\boldsymbol{\Sigma}|\boldsymbol{\Psi})$ が次のように与えられるなら、

$$
\begin{aligned}
\boldsymbol{\Psi}&\sim \textrm{W}_p(n_1, \mathbf{B})\\
\boldsymbol{\Sigma}|\boldsymbol{\Psi}&\sim \textrm{IW}_p(n_2, \boldsymbol{\Psi}),
\end{aligned}
$$

その場合、$\boldsymbol{\Sigma}$ の周辺分布は $\textrm{MF}_{p}(n_1/2,n_2/2,\mathbf{B})$ です。
