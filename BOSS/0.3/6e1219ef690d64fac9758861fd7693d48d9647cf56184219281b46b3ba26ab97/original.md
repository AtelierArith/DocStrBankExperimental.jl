```
GaussianProcess(; kwargs...)
```

A Gaussian Process surrogate model. Each output dimension is modeled by a separate independent process.

# Keywords

  * `mean::Union{Nothing, Function}`: Used as the mean function for the GP.       Defaults to `nothing` equivalent to `x -> zeros(y_dim)`.
  * `kernel::Kernel`: The kernel used in the GP. Defaults to the `Matern32Kernel()`.
  * `length_scale_priors::LengthScalePriors`: The prior distributions       for the length scales of the GP. The `length_scale_priors` should be a vector       of `y_dim` `x_dim`-variate distributions where `x_dim` and `y_dim` are       the dimensions of the input and output of the model respectively.
  * `amp_priors::AmplitudePriors`: The prior distributions       for the amplitude hyperparameters of the GP. The `amp_priors` should be a vector       of `y_dim` univariate distributions.
  * `noise_std_priors::NoiseStdPriors`: The prior distributions       of the noise standard deviations of each `y` dimension.
