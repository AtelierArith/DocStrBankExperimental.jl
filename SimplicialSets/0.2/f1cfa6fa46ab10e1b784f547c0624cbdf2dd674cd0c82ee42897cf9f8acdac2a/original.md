```
isdegenerate(x::AbstractSimplex, k0::Integer, k1::Integer) -> Bool
```

Return `true` if `x` is degenerate on the interval `k0:k1` and `false` otherwise. The indices must satisfy `0 <= k0 <= k1 <= dim(x)`.

A simplex is degenerate on the interval `k0:k1` if it degenerate at some position `k` between `k0` and `k1-1`.
