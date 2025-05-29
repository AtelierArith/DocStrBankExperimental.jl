```
BootstrapConfidenceInterval(lower, upper, quantile, bootstrap)
```

A type representing the `lower` and `upper` bounds of an effect size confidence interval at a specified `quantile` with `bootstrap` resamples.

```
BootstrapConfidenceInterval(f, xs, ys, bootstrap; quantile)
```

Calculate a bootstrap confidence interval between two vectors `xs` and `ys` at a specified `quantile` by applying `f` to `bootstrap` resamples of `xs` and `ys`.
