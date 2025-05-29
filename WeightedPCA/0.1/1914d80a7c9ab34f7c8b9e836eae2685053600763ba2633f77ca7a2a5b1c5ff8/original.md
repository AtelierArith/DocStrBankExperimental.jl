```
wpca(Y, i, weights=UniformWeights())
```

Compute `i`th principal component of data `Y` via weighted PCA using `weights`, i.e., output is the `i`th eigenvector of the weighted sample covariance `Σ_l w[l] Y[l]*Y[l]'`. Data `Y` is a list of matrices (each column is a sample).

# Choices for `weights`

  * `UniformWeights()` : uniform weights, i.e., `w[l] = 1` [default]
  * `InverseVarianceWeights([v])` : inverse noise variance weights, i.e., `w[l] = 1/v[l]`
  * `OptimalWeights([v,λ])` : optimal weights for signal with variance `λ`, i.e., `w[l] = 1/v[l] * 1/(1+v[l]/λ)`

The `weights` can also be manually set by passing in an `AbstractVector{<:Real}`.

See also: [`UniformWeights`](@ref), [`InverseVarianceWeights`](@ref), [`OptimalWeights`](@ref).
