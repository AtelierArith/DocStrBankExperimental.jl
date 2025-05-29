```
series(w::AbstractVector, P::AbstractMatrix, X, d::Int64) -> Series{C,M}
```

Compute the series of the moment sequence $∑_i ω_{i} P_{i}^α$ for $|α| \leq d$.
