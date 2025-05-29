```
sparse_row(R::Ring, J::Vector{Tuple{Int, T}}) -> SRow{T}
```

スパース行 $(a_i)_i$ を構築します。ここで $a_{i_j} = x_j$ であり、$J = (i_j, x_j)_j$ です。要素 $x_i$ は環 $R$ に属する必要があります。
