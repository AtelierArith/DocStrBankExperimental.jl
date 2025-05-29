```
seasonal_decomposition(A::ClimArray, fs = [1, 2]) → seasonal, residual
```

Decompose `A` into a seasonal and residual components, where the seasonal contains the periodic parts of `A`, with frequencies given in `fs`, and residual contains what's left.

`fs` is measured in 1/year. This function works even for non-equispaced time axis (e.g. monthly averages) and uses LPVSpectral.jl and SignalDecomposition.jl.
