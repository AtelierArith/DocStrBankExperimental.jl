`coxeter_matrix(W)` or `coxmat`

returns the Coxeter matrix of the Coxeter group `W`, that is the matrix `m` whose  entry `m[i,j]` contains the order of `W(i)*W(j)` where `W(i)` is the `i`-th  Coxeter generator of  `W`. An infinite  order is represented by the entry `0`.

```julia-repl
julia> W=coxsym(4)
𝔖 ₄

julia> coxmat(W)
3×3 Matrix{Int64}:
 1  3  2
 3  1  3
 2  3  1
```
