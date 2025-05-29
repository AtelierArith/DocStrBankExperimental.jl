```
logdensity_rel(m1, m2, x)
```

Compute the log-density of `m1` relative to `m2` at `x`. This function checks whether `x` is in the support of `m1` or `m2` (or both, or neither). If `x` is known to be in the support of both, it can be more efficient to call `unsafe_logdensity_rel`. 
