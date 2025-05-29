```
MonteCarloEntropy()
```

Monte Carlo estimation of the entropy.

# Requirements

  * The variational approximation `q` implements `logpdf`.
  * `logpdf(q, η)` must be differentiable by the selected AD framework.
