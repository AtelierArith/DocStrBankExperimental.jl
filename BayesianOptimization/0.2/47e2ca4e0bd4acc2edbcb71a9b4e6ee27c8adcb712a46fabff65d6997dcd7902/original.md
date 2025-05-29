The expected improvement measures the expected improvement `x - τ` of a point `x` upon an incumbent target `τ`. For Gaussian distributions it is given by

```
(μ(x) - τ) * ϕ[(μ(x) - τ)/σ(x)] + σ(x) * Φ[(μ(x) - τ)/σ(x)]
```

where `ϕ` is the standard normal distribution function and `Φ` is the standard normal cumulative function, and `μ(x)`, `σ(x)` are mean and standard deviation of the distribution at point `x`.
