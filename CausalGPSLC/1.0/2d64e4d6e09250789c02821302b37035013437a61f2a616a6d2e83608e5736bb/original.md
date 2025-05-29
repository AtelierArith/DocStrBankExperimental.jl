```
conditionalITE(nothing, nothing, tyLS, yNoise, yScale, nothing, nothing, T, Y, doT)
conditionalITE(nothing, xyLS, tyLS, yNoise, yScale, nothing, X, T, Y, doT)
conditionalITE(uyLS, nothing, tyLS, yNoise, yScale, U, nothing, T, Y, doT)
conditionalITE(uyLS, xyLS, tyLS, yNoise, yScale, U, X, T, Y, doT)
```

Conditional Individual Treatment Estimation

`conditionalITE` takes in parameters (presumably from posterior inference) as well as the observed and inferred data to produce individual treatment  effects.

Params:

  * `uyLS`: (optional) Kernel lengthscale for latent confounders to outcome
  * `xyLS`: (optional) Kernel lengthscale for covariates to outcome
  * `tyLS`: Kernel lengthscale for treatment to outcome
  * `yNoise`: Gaussian noise for outcome prediction
  * `yScale`: Gaussian scale for outcome prediction
  * `U`: (optional) Latent confounders
  * `X`: (optional) Covariates
  * `T`: Treatment
  * `Y`: Outcome
  * `doT`: Treatment intervention

Returns:

  * `MeanITE::Vector{Float64}`: The mean value for the `n` individual treatment effects
  * `CovITE::Matrix{Float64}`: The covariance matrix for the `n` individual treatment effects.
