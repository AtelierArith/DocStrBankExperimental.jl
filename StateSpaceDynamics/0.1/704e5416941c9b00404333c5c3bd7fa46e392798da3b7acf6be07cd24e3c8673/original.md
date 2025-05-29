```
fit!(pmm::PoissonMixtureModel, data::Matrix{Int}; <keyword arguments>)
```

Fits a Poisson Mixture Model (PMM) to the given data using the Expectation-Maximization (EM) algorithm.

# Arguments

  * `pmm::PoissonMixtureModel`: The Poisson Mixture Model to be fitted.
  * `data::Matrix{Int}`: The dataset on which the model will be fitted, where each row represents a data point.
  * `maxiter::Int=50`: The maximum number of iterations for the EM algorithm (default: 50).
  * `tol::Float64=1e-3`: The tolerance for convergence. The algorithm stops if the change in log-likelihood between iterations is less than this value (default: 1e-3).
  * `initialize_kmeans::Bool=false`: If true, initializes the means of the PMM using K-means++ initialization (default: false).

# Returns

  * `class_probabilities`: A matrix where each entry (i, k) represents the probability of the i-th data point belonging to the k-th component of the mixture model.

# Example

```julia
data = rand(1:10, 100, 1)  # Generate some random integer data
pmm = PoissonMixtureModel(k=3)  # Initialize a PMM with 3 components
class_probabilities = fit!(pmm, data, maxiter=100, tol=1e-4, initialize_kmeans=true)
```
