```
colored_noise(rng = Random.default_rng(); n::Int = 500, ρ, σ = 0.1, transform = true)
```

Generate `n` points of colored noise. `ρ` is the desired correlation between adjacent samples. The noise is drawn from a normal distribution with zero mean and standard deviation `σ`. If `transform  = true`, then transform data using aquadratic nonlinear static distortion.
