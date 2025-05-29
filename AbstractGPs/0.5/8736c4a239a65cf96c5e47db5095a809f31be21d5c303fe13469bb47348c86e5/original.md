```
mean_and_var(f::AbstractGP, x::AbstractVector)
```

Compute both `mean(f(x))` and the diagonal elements of `cov(f(x))`. Sometimes more efficient than computing them separately, particularly for posteriors.
