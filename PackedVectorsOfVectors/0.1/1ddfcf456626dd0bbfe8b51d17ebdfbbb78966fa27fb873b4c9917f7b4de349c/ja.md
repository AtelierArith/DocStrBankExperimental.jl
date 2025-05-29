```
packed_zeros([T=Float64,] n) -> pv::PackedVectorOfVectors
```

`pv[k] == zeros(T, nth(n,k))` となるように、ベクトルのパックを作成します。
