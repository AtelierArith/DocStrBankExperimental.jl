```
sparse_row(R::Ring, J::Vector{Tuple{Int, Int}}) -> SRow
```

$$
R
$$

上のスパース行 $(a_i)_i$ を構築し、$J = (i_j, x_j)_j$ の場合に $a_{i_j} = x_j$ となります。
