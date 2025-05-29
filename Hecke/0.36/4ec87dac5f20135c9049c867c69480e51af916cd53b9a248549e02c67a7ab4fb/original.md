```
sparse_row(R::Ring, J::Vector{Tuple{Int, Int}}) -> SRow
```

Constructs the sparse row $(a_i)_i$ over $R$ with $a_{i_j} = x_j$, where $J = (i_j, x_j)_j$.
