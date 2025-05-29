```
Normalize(lb, ub)
```

Performs min-max scaling of the input according to `(x - lb) / (ub - lb)`. The  length of `lb` and `ub` should match the input vector.

# Arguments:

  * `lb`: lower bound, default = zero(ub).
  * `ub`: upper bound.
