```
predict(M::PCA, x::AbstractVecOrMat{<:Real})
```

Given a PCA model `M`, transform observations `x` into principal components space, as

$$
\mathbf{y} = \mathbf{P}^T (\mathbf{x} - \boldsymbol{\mu})
$$

Here, `x` can be either a vector of length `d` or a matrix where each column is an observation, and `\mathbf{P}` is the projection matrix.
