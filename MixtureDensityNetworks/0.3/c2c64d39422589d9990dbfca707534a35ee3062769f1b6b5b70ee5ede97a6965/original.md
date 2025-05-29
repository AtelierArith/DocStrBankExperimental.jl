```julia
likelihood_loss(
    distributions::Vector{<:Distributions.MixtureModel{Distributions.Multivariate}},
    y::Matrix{<:Real}
) -> Any

```

Conpute the negative log-likelihood loss for a set of labels `y` under a set of multivariate Gaussian Mixture Models.

# Parameters

  * `distributions`: A vector of multivariate Gaussian Mixture Model distributions.
  * `y`: A dxn matrix of labels where d is the dimension of each label and n is the number of samples.
