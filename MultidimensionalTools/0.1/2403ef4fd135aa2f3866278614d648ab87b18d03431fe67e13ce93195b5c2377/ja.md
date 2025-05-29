```
n_adjacencies(dim::Int) -> Int
n_adjacencies(M::AbstractArray) -> Int
```

行列または次元を指定すると、無限格子/行列内の任意の要素に隣接する要素の数を返します（すなわち、エッジを含まない）。エッジについては、``を参照してください。
