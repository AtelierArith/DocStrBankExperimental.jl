```
 partition(c; k, endpoints)
```

Partition `c::Corpus` into a `Vector{Corpus}` of length `k` (by default, 40). Or supply  a vector of predefined `endpoints` for the partitions, in which case `k` is ignored.
