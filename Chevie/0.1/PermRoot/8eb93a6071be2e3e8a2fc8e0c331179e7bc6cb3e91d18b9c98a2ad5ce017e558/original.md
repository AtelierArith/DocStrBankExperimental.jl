`reflection_eigenvalues(W)` or `refleigen(W)`

Let `W` be a reflection group on the vector space `V`. `reflection_eigenvalues(W)` returns for each conjugacy class representative `x`  of `W` (see `classreps`)  the eigenvalues of `x`  on `V`, as a list of `Root1`.

```julia-repl
julia> refleigen(coxgroup(:B,2))
5-element Vector{Vector{Root1}}:
 [1, 1]
 [-1, 1]
 [-1, -1]
 [-1, 1]
 [ζ₄³, ζ₄]
```
