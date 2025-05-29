```
packed_ones([T=Float64,] n) -> pv::PackedVectorOfVectors
```

`pv[k] == ones(T, nth(n,k))` となるように、ベクトルのパックを作成します。
