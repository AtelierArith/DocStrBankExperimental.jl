```julia
MultivariateGMM(
    input::Int64,
    output::Int64,
    mixtures::Int64
) -> MixtureDensityNetworks.MultivariateGMM

```

Construct a layer which returns a multivariate Gaussian Mixture Model as its output.

# Parameters

  * `input`: Specifies the length of the feature vectors. The layer expects a matrix with the dimensions `input x N` as input.
  * `output`: Specifies the length of the label vectors. The layer returns a matrix with dimensions `output x N` as output.
  * `mixtures`: The number of mixtures to use in the GMM.
