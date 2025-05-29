```
LowRankMatPol(lambda::Vector, vs::Vector{Vector}[, ws::Vector{Vector}])
```

The matrix $∑_i λ_i v_i w_i^{\sf T}$ where $v_i$ are the entries of `vs` and $w_i$ the entries of `ws`

If `ws` is not specified, use `ws = vs`.
