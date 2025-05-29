```
mean_and_cov(f::AbstractGP, x::AbstractVector)
```

Compute both `mean(f(x))` and `cov(f(x))`. Sometimes more efficient than computing them separately, particularly for posteriors.
