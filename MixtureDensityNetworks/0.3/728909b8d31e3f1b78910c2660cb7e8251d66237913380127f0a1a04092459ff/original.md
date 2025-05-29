```julia
likelihood_loss(
    distributions::Vector{<:Distributions.MixtureModel{Distributions.Univariate}},
    y::Matrix{<:Real}
) -> Any

```

Conpute the negative log-likelihood loss for a set of labels `y` under a set of univariate Gaussian Mixture Models.

# Parameters

  * `distributions`: A vector of univariate Gaussian Mixture Model distributions.
  * `y`: A 1xn matrix of labels where n is the number of samples.
