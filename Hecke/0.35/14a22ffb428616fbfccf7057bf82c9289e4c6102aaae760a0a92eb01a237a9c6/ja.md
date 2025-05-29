```
sparse_row(R::NCRing, J::Vector{Int}, V::Vector{T}) -> SRow{T}
```

$$
R
$$

上のスパース行$(a_i)_i$を構築し、$J = (i_j)_j$および$V = (x_j)_j$に対して$a_{i_j} = x_j$となります。
