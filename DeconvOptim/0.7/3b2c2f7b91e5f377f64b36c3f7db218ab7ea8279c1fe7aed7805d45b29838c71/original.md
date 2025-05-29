```
gauss_aux(μ, meas, storage=similar(μ))
```

Calculates the Gauss loss for `μ` and `meas`. `μ` can be of larger size than `meas`. In that case we extract a centered region from `μ` of the same size as `meas`.
