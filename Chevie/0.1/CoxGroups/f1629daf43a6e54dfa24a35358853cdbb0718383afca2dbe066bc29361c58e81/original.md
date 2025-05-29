`words(W::CoxeterGroup,w)`

returns  the list  of all  reduced expressions  of the  element `w`  of the Coxeter group `W`.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> words(W,longest(W))
16-element Vector{Vector{Int64}}:
 [1, 2, 1, 3, 2, 1]
 [1, 2, 3, 1, 2, 1]
 [1, 2, 3, 2, 1, 2]
 [1, 3, 2, 1, 3, 2]
 [1, 3, 2, 3, 1, 2]
 [2, 1, 2, 3, 2, 1]
 [2, 1, 3, 2, 1, 3]
 [2, 1, 3, 2, 3, 1]
 [2, 3, 1, 2, 1, 3]
 [2, 3, 1, 2, 3, 1]
 [2, 3, 2, 1, 2, 3]
 [3, 1, 2, 1, 3, 2]
 [3, 1, 2, 3, 1, 2]
 [3, 2, 1, 2, 3, 2]
 [3, 2, 1, 3, 2, 3]
 [3, 2, 3, 1, 2, 3]
```
