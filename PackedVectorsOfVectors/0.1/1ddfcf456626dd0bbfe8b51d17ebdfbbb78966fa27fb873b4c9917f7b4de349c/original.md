```
packed_zeros([T=Float64,] n) -> pv::PackedVectorOfVectors
```

Create a packed vector of vectors such that `pv[k] == zeros(T, nth(n,k))`.
