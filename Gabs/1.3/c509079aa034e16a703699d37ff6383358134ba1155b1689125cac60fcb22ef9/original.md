```
williamson(state::GaussianState) -> Williamson
```

Compute the williamson decomposition of the `covar` field of a `GaussianState` object and return a `Williamson` object.

A symplectic matrix `S` and symplectic spectrum `spectrum` can be obtained via `F.S` and `F.spectrum`.

Iterating the decomposition produces the components `S` and `spectrum`.

To compute only the symplectic spectrum of a Gaussian state, call [`sympspectrum`](@ref).
