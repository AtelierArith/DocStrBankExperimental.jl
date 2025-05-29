```
StickingTheLandingEntropy()
```

The "sticking the landing" entropy estimator[^RWD2017].

# Requirements

  * The variational approximation `q` implements `logpdf`.
  * `logpdf(q, η)` must be differentiable by the selected AD framework.
