```
predict(M::CCA, Z::AbstractVecOrMat{<:Real}, c::Symbol)
```

Given a [`CCA`](@ref) model, one can transform observations into both spaces into a common space, as

$$
\mathbf{z}_x = \mathbf{P}_x^T (\mathbf{x} - \boldsymbol{\mu}_x) \\
\mathbf{z}_y = \mathbf{P}_y^T (\mathbf{y} - \boldsymbol{\mu}_y)
$$

Here, $\mathbf{P}_x$ and $\mathbf{P}_y$ are projection matrices for $X$ and $Y$; $\boldsymbol{\mu}_x$ and $\boldsymbol{\mu}_y$ are mean vectors.

Parameter `Z` can be either a vector of length `dx`, `dy`, or a matrix where each column is an observation. The component parameter `c` can be `:x` or `:y`.
