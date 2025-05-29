```julia
MixtureDensityNetwork(
    input::Int64,
    output::Int64,
    layers::Vector{Int64},
    mixtures::Int64
) -> Union{MixtureDensityNetworks.MixtureDensityNetwork{MixtureDensityNetworks.MultivariateGMM}, MixtureDensityNetworks.MixtureDensityNetwork{MixtureDensityNetworks.UnivariateGMM}}

```

Construct a standard Mixture Density Network.

# Parameters

  * `input`: The dimension of the input features.
  * `output`: The dimension of the output. Setting output = 1 indicates a univariate model, whereas output > 1 indicates a multivariate model.
  * `layers`: The topolgy of the hidden layers, starting from the first layer.
  * `mixtures`: The number of Gaussian mixtures to use in the predicted distribution.
