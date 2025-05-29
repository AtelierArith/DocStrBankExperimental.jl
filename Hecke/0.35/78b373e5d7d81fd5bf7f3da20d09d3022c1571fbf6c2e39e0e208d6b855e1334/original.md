```
sparse_row(R::Ring, J::Vector{Tuple{Int, T}}) -> SRow{T}
```

Constructs the sparse row $(a_i)_i$ with $a_{i_j} = x_j$, where $J = (i_j, x_j)_j$. The elements $x_i$ must belong to the ring $R$.
