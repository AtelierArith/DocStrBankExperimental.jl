```
dispersion(c; k = 40, kwargs...)
```

Get a `BitMatrix` representing the dispersion of `c`'s vocabulary over `k`  equally sized partitions. The result will be of dimensions `V(c) x k`.

Rather than specifying `k`, you may instead pass in a vector of `endpoints`. (See `partition` for details.)
