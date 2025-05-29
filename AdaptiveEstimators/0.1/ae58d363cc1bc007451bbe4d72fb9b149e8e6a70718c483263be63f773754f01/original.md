```
fit!(model::SystemModel, alg::Estimator, x, y; saveat, rng)
fit!(model::SystemModel, alg::Estimator, x, y, nsteps, decision; ...)
```

Estimate `model` parameters using `alg` adaptive algorithm. Input `x` and desired output `y` are vectors (scalar input/output) or matrices (vector input/output) with the last dimension being the time dimension. Input `x` is assumed to be available at all time indices `1:nsteps`. Desired output `y` may be available at all time indices or for a shorter time. If it is available for a shorter time, the estimator will use a `decision` function to generated desired output in a decision-directed mode for the rest of the time.

The `saveat` argument specifies how often to record parameter history. Random number generator `rng` is used to initialize model and estimator.

Returns `EstimationResults` containing estimated paramaters `p`, parameter history `phist`, model outputs `y` and loss history `loss`.
