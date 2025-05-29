```
assigndist_normal(μ, lower, upper; nσ = 1,
    trunc_lower = -Inf, trunc_upper = Inf,
    tolerance = 1e-2μ)
```

Assign parameters to a Normal distribution based on location parameter `μ`, together with `lower` and `upper` uncertainty bounds. `nσ` indicates how many standard deviations away from `μ` `lower`/`upper` are (they must be equidistant from `μ`). `trunc_lower` and `trunc_upper` truncated the distribution if specified (defaults to `-Inf` and `Inf`).
