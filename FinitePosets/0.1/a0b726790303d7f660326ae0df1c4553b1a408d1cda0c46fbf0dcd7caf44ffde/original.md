`moebius_matrix(P::CPoset)`  the  matrix  of  the  Moebius  function  `μ(x,y)`  (the inverse of the ζ or incidence matrix)

```julia-repl
julia> moebius_matrix(CPoset(:diamond,5))
5×5 Matrix{Int64}:
 1  -1  -1  -1   2
 0   1   0   0  -1
 0   0   1   0  -1
 0   0   0   1  -1
 0   0   0   0   1
```

`moebius_matrix(P::Poset)` returns `moebius_matrix(P.C)`
