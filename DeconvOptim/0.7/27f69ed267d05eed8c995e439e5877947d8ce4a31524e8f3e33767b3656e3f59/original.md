```
anscombe_aux(μ, meas, storage=similar(μ); b=0)
```

Calculates the Poisson loss using the Anscombe-based norm for `μ` and `meas`. `μ` can be of larger size than `meas`. In that case we extract a centered region from `μ` of the same size as `meas`. `b=0` is the optional parameter under the `√`. Note that the data will be normalized to the mean of the data, which means that you have to divide this parameter also by the mean of the data, i.e. b=3.0/8.0/mean(measured).
