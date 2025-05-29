```
MvLogitNormal{<:AbstractMvNormal}
```

The [multivariate logit-normal distribution](https://en.wikipedia.org/wiki/Logit-normal_distribution#Multivariate_generalization) is a multivariate generalization of [`LogitNormal`](@ref) capable of handling correlations between variables.

If $\mathbf{y} \sim \mathrm{MvNormal}(\boldsymbol{\mu}, \boldsymbol{\Sigma})$ is a length $d-1$ vector, then

$$
\mathbf{x} = \operatorname{softmax}\left(\begin{bmatrix}\mathbf{y} \\ 0 \end{bmatrix}\right) \sim \mathrm{MvLogitNormal}(\boldsymbol{\mu}, \boldsymbol{\Sigma})
$$

is a length $d$ probability vector.

```julia
MvLogitNormal(μ, Σ)                 # MvLogitNormal with y ~ MvNormal(μ, Σ)
MvLogitNormal(MvNormal(μ, Σ))       # same as above
MvLogitNormal(MvNormalCanon(μ, J))  # MvLogitNormal with y ~ MvNormalCanon(μ, J)
```

# Fields

  * `normal::AbstractMvNormal`: contains the $d-1$-dimensional distribution of $y$
