```
truncate(uv::TheoreticalDistributionScalarValue,
    constraint::TruncateStd, n::Int = 10000)
```

Truncate the theoretical distribution furnishing `uv` using a `TruncateStd` sampling constraint. 

This functions needs to compute the mean and standard deviation  of a truncated distribution, so takes an extra optional argument `n_draws` to allow  this.
