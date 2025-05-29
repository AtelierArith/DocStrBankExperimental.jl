```
isstable(model,p,T,z)::Bool
```

Performs stability tests for a (p,T,z) pair, and warn if any tests fail. returns `true/false`.

Checks, in order of complexity:

  * mechanical stability: isothermal compressibility is not negative.
  * diffusive stability: all eigenvalues of `∂²A/∂n²` are positive.
  * chemical stability: there isn't any other combinations of compositions at p(V,T),T that are more stable than the input composition.

For checking (V,T,z) pairs, use `Clapeyron.VT_isstable(model,V,T,z)` instead.
