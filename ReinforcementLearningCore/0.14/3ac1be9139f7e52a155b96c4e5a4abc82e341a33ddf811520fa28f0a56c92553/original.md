```
mvnormlogpdf(μ::AbstractVecOrMat, L::AbstractMatrix, x::AbstractVecOrMat)
```

GPU compatible and automatically differentiable version for the logpdf function of multivariate normal distributions.  Takes as inputs `mu` the mean vector, `L` the lower triangular matrix of the cholesky decomposition of the covariance matrix, and `x` a matrix of samples where each column is a sample.  Return a Vector containing the logpdf of each column of x for the `MvNormal` parametrized by `μ` and `Σ = L*L'`.
