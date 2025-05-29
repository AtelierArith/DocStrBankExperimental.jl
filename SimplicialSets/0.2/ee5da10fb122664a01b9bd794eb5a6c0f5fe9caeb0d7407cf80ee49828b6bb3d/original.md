```
isdegenerate(x::AbstractSimplex, k::Integer) -> Bool
```

Return `true` if `x` is degenerate at position `k` and `false` otherwise. The index `k` must be between `0` and `dim(x)-1`.

A simplex `x` of positive dimension is degenerate at position `k` if `x == s(d(x, k), k)`.
