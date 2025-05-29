```
reconstruct(M::PCA, y::AbstractVecOrMat{<:Real})
```

Given a PCA model `M`, returns a (approximately) reconstructed observations from principal components space, as

$$
\tilde{\mathbf{x}} = \mathbf{P} \mathbf{y} + \boldsymbol{\mu}
$$

Here, `y` can be either a vector of length `p` or a matrix where each column gives the principal components for an observation, and $\mathbf{P}$ is the projection matrix.
