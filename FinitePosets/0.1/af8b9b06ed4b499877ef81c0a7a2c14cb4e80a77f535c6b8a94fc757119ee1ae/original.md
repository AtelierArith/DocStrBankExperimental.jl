`coxeter_matrix(p)` the Coxeter matrix of the `Poset` or `CPoset`, defined as `-m*transpose(inv(m))` where `m` is the ζ or incidence matrix.

```julia-repl
julia> coxeter_matrix(CPoset(:diamond,5))
5×5 Matrix{Int64}:
  0  0  0  0  -1
 -1  0  1  1  -1
 -1  1  0  1  -1
 -1  1  1  0  -1
 -2  1  1  1  -1
```
