```
fit!(gmm::GaussianMixtureModel, data::Matrix{<:Real}; <keyword arguments>)
```

Fits a Gaussian Mixture Model (GMM) to the given data using the Expectation-Maximization (EM) algorithm.

# Arguments

  * `gmm::GaussianMixtureModel`: The Gaussian Mixture Model to be fitted.
  * `data::Matrix{<:Real}`: The dataset on which the model will be fitted, where each row represents a data point.
  * `maxiter::Int=50`: The maximum number of iterations for the EM algorithm (default: 50).
  * `tol::Float64=1e-3`: The tolerance for convergence. The algorithm stops if the change in log-likelihood between iterations is less than this value (default: 1e-3).
  * `initialize_kmeans::Bool=false`: If true, initializes the means of the GMM using K-means++ initialization (default: false).

# Returns

  * `class_probabilities`: A matrix where each entry (i, k) represents the probability of the i-th data point belonging to the k-th component of the mixture model.

# Example

```julia
data = rand(2, 100)  # Generate some random data
gmm = GaussianMixtureModel(k=3, d=2)  # Initialize a GMM with 3 components and 2-dimensional data
class_probabilities = fit!(gmm, data, maxiter=100, tol=1e-4, initialize_kmeans=true)
```
