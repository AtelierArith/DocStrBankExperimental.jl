```
beta_uniform(theta::Real, alpha::Real, beta::Real)
```

Samples a `Float64` value from a mixture of a uniform distribution on [0, 1] with probability `1-theta` and a beta distribution with parameters `alpha` and `beta` with probability `theta`.
