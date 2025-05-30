```
InverseWishart(ν, Ψ)
```

```julia
ν::Real           自由度 (p - 1 より大きい)
Ψ::AbstractPDMat  p x p スケール行列
```

[逆ウィシャート分布](http://en.wikipedia.org/wiki/Inverse-Wishart_distribution)は、逆ガンマ分布を$p\times p$の実数、正定値行列$\boldsymbol{\Sigma}$に一般化します。もし$\boldsymbol{\Sigma}\sim \textrm{IW}_p(\nu,\boldsymbol{\Psi})$であれば、その確率密度関数は次のようになります。

$$
f(\boldsymbol{\Sigma}; \nu,\boldsymbol{\Psi}) =
\frac{\left|\boldsymbol{\Psi}\right|^{\nu/2}}{2^{\nu p/2}\Gamma_p(\frac{\nu}{2})} \left|\boldsymbol{\Sigma}\right|^{-(\nu+p+1)/2} e^{-\frac{1}{2}\operatorname{tr}(\boldsymbol{\Psi}\boldsymbol{\Sigma}^{-1})}.
$$

$$
\mathbf{H}\sim \textrm{W}_p(\nu, \mathbf{S})
$$

であることは、$\mathbf{H}^{-1}\sim \textrm{IW}_p(\nu, \mathbf{S}^{-1})$ であることと同値です。
