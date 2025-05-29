```julia
UnivariateGMM(
    input::Int64,
    mixtures::Int64
) -> MixtureDensityNetworks.UnivariateGMM

```

Construct a layer which returns a univariate Gaussian Mixture Model as its output.

# Parameters

  * `input`: Specifies the length of the feature vectors. The layer expects a matrix with the dimensions `input x N` as input.
  * `mixtures`: The number of mixtures to use in the GMM.
