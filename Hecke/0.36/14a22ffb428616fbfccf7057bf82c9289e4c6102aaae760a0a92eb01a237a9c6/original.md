```
sparse_row(R::NCRing, J::Vector{Int}, V::Vector{T}) -> SRow{T}
```

Constructs the sparse row $(a_i)_i$ over $R$ with $a_{i_j} = x_j$, where $J = (i_j)_j$ and $V = (x_j)_j$.
