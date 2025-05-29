```
rinit(object; t0=timezero(object), params=coef(object), nsim=1)
```

`rinit` is the workhorse for the simulator of the initial-state distribution.

## Arguments

  * `object`: the PompObject
  * `params`: a NamedTuple of parameters or vector of NamedTuples
  * `t0`: the time at which `rinit` is to be simulated. This should be a single scalar.
  * `nsim`: the number of simulations desired.
