```
DiffusionStateModel(f::Function, g::Function, init)
```

Returns a diffusion process hidden state model $dX_t = f(X_t)dt + g(X_t)dW_t$, where $f$ is the `drift_function`, $g$ is the `observation_function`, $X_t$ is the $n$-dimensional hidden state at time $t$, and $W_t$ is an $m$-dimensional Brownian motion process.

Argument `init` stands for the initial condition of the process, which is either

  * A vector of length `n` for a fixed (deterministic) initial condition
  * A `Distributions.Sampleable` type for a random initial condition
