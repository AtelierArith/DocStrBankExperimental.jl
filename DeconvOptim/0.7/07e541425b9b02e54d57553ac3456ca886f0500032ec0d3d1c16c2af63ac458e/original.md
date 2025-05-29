```
scaled_gauss_aux(μ, meas, storage=similar(μ); read_var=0)
```

Calculates the scaled Gauss loss for `μ` and `meas`. `read_var=0` is the readout noise variance of the sensor. `μ` can be of larger size than `meas`. In that case we extract a centered region from `μ` of the same size as `meas`.
