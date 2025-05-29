```
function promote_to_nD(M::Array{T, N}, n::Int, fill_elem::T)
```

Assumes the given matrix M is an (n - 1) dimensional slice of an n-dimensional structure, and fills in the array to n dimensions with `fill_elem`.
