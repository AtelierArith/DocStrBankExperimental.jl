```
Gaussian(μ, Σ) -> P
```

Gaussian distribution with mean `μ` and covariance `Σ`. Defines `rand(P)` and `(log-)pdf(P, x)`. Designed to work with `Number`s, `UniformScaling`s, `StaticArrays` and `PSD`-matrices.

Implementation details: On `Σ` the functions `logdet`, `whiten` and `unwhiten` (or `chol` as fallback for the latter two) are called.
