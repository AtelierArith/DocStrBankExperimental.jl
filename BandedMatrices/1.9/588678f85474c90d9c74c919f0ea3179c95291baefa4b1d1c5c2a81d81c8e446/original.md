```
BandedMatrix{T}(kv::Pair, (m,n), (l,u))
```

Construct a m × n BandedMatrix with bandwidths (l,u) from `Pair`s of diagonals and vectors. Vector `kv.second` will be placed on the `kv.first` diagonal.
