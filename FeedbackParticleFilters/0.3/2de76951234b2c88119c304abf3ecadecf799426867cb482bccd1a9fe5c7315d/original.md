```
LinearDiffusionStateModel(A, B; init)
```

Returns a linear diffusion process hidden state model $dX_t = A X_t dt + B dW_t$ with appropriately sized matrices $A$ and $B$.

Optional argument `init` stands for the initial condition of the process, which is either

  * A vector of length `n` for a fixed (deterministic) initial condition
  * A `Distributions.Sampleable` type for a random initial condition

If argument `init` is left out, it is set to either 

  * a multivariate normal distribution with covariance matrix set to the stationary variance, if it exists
  * the zero vector
