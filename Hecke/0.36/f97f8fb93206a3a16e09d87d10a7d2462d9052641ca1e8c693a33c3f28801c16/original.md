```
gram_matrix_of_generators(L::AbstractLat; minimal::Bool = false) -> MatElem
```

Return the Gram matrix of a generating set of the lattice `L`.

If `minimal == true`, then a minimal generating set is used. Note that computing minimal generators is expensive.
