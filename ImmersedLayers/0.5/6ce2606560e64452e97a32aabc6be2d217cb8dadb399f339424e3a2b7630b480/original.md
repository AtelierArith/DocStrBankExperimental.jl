```
integrate(u::GridData,cache::BasicILMCache)
```

Calculate the discrete volume integral of grid data `u`. If `u` is `VectorGridData`, then this returns a vector of the integrals in each coordinate direction. This integral produces the same result regardless if `GridScaling` or `IndexScaling` is used.
