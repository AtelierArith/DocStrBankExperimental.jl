```
size(s::Sampleable)
```

The size (i.e. shape) of each sample. Always returns `()` when `s` is univariate, and `(length(s),)` when `s` is multivariate.
