```
build_pyhf(load_pyhfjson(path)) -> PyHFModel
```

the `expected(αs)` is a function that takes vector or tuple of length `N`, where `N` is also the length of `priors` and `priornames`. In other words, these three fields of the returned object are aligned.

!!! note
    The bins from different channels are put into a `NTuple{Nbins, Vector}`.

