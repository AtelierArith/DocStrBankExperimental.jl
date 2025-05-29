```julia
two_sided_pvalues(ubc; ess_correction)

```

Calculate two-sided p-values for bin counts.

Uses a normal approxiation with continuity correction.

When `ess_correction = true` (the default), the standard deviation is calculated using the the effective sample size.
