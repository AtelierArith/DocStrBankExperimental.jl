```
moment(w::Vector{C}, P::Matrix{C}) -> Vector{Int64} -> C
```

Compute the moment function $α -> ∑_{i} ω_{i} P_{i}^α$ associated to the sequence P of r points of dimension n, which is a matrix of size r*n and the weights w.
