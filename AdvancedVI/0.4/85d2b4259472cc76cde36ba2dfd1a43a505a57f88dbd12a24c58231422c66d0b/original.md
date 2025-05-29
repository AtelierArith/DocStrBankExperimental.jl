```
StickingTheLandingEntropyZeroGradient()
```

The "sticking the landing" entropy estimator[^RWD2017] but modified to have a gradient of mean zero. This is expected to be used only with `ProximalLocationScaleEntropy`.

# Requirements

  * The variational approximation `q` implements `logpdf`.
  * `logpdf(q, η)` must be differentiable by the selected AD framework.
  * The variational approximation implements `entropy`.
