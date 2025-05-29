```
MvLogitNormal{<:AbstractMvNormal}
```

[multivariate logit-normal distribution](https://en.wikipedia.org/wiki/Logit-normal_distribution#Multivariate_generalization)は、変数間の相関を扱うことができる[`LogitNormal`](@ref)の多変量一般化です。

もし$\mathbf{y} \sim \mathrm{MvNormal}(\boldsymbol{\mu}, \boldsymbol{\Sigma})$が長さ$d-1$のベクトルであるなら、

$$
\mathbf{x} = \operatorname{softmax}\left(\begin{bmatrix}\mathbf{y} \\ 0 \end{bmatrix}\right) \sim \mathrm{MvLogitNormal}(\boldsymbol{\mu}, \boldsymbol{\Sigma})
$$

は長さ$d$の確率ベクトルです。

```julia
MvLogitNormal(μ, Σ)                 # MvLogitNormal with y ~ MvNormal(μ, Σ)
MvLogitNormal(MvNormal(μ, Σ))       # same as above
MvLogitNormal(MvNormalCanon(μ, J))  # MvLogitNormal with y ~ MvNormalCanon(μ, J)
```

# フィールド

  * `normal::AbstractMvNormal`: $y$の$d-1$次元分布を含む
