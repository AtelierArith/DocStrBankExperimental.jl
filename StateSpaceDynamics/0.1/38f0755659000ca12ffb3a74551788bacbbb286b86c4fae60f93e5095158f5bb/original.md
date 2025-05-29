```
GaussianMixtureModel
```

A Gaussian Mixture Model for clustering and density estimation.

# Fields

  * `k::Int`: Number of clusters.
  * `μₖ::Matrix{<:Real}`: Means of each cluster (dimensions: data_dim x k).
  * `Σₖ::Array{Matrix{<:Real}, 1}`: Covariance matrices of each cluster.
  * `πₖ::Vector{Float64}`: Mixing coefficients for each cluster.

# Examples

```julia
gmm = GaussianMixtureModel(3, 2) # Create a Gaussian Mixture Model with 3 clusters and 2-dimensional data
fit!(gmm, data)
```
