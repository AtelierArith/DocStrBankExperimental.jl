```
path_to_matrix(g::GridGraph, path::Vector{<:Integer})
```

Store the shortest `s -> d` path in `g` as an integer matrix of size `height(g) * width(g)`, where entry `(i,j)` counts the number of visits to the associated vertex.
