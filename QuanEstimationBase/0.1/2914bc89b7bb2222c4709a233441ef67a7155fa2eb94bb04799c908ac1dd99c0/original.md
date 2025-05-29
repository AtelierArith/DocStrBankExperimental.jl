```
GRAPE(;max_episode=300, epsilon=0.01, beta1=0.90, beta2=0.99, Adam::Bool=true)
```

Control optimization algorithm: GRAPE.

  * `max_episode`: The number of episodes.
  * `epsilon`: Learning rate.
  * `beta1`: The exponential decay rate for the first moment estimates.
  * `beta2`: The exponential decay rate for the second moment estimates.
  * `Adam`: Whether or not to use Adam for updating control coefficients.
