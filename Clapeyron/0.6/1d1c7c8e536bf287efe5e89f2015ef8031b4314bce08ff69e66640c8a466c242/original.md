```
VT_diffusive_stability(model,V,T,z)::Bool
```

Performs a diffusive stability for a (V,T,z) pair, returns `true/false`. Checks if all eigenvalues of `∂²A/∂n²` are positive. Returns `false` if the eos calculation failed. this normally occurs when evaluating on densities lower than the maximum density (given by `Clapeyron.lb_volume(model,T,z)`)
