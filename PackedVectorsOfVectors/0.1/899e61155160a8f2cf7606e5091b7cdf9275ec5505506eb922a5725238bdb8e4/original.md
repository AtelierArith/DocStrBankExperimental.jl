```
packed_ones([T=Float64,] n) -> pv::PackedVectorOfVectors
```

Create a packed vector of vectors such that `pv[k] == ones(T, nth(n,k))`.
