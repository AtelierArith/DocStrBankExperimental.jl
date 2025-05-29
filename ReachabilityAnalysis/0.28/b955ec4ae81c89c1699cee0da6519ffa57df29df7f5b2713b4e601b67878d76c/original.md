```
shift(fp::Flowpipe{N, <:AbstractReachSet}, t0::Number) where {N}
```

Return the time-shifted flowpipe by the given number.

### Input

  * `fp` – flowpipe
  * `t0` – time shift

### Output

A new flowpipe such that the time-span of each constituent reach-set has been shifted by `t0`.
