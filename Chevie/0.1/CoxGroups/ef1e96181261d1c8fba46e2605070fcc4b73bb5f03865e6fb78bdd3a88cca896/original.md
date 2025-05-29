`inversions(W,w)`

Returns  the inversions of the element `w` of the finite Coxeter group `W`, that  is, the list of the  indices of reflections `r` of `W` such that `l(rw)<l(w)` where `l` is the Coxeter length.

```julia-repl
julia> W=coxgroup(:A,3)
A₃

julia> inversions(W,W(1,2,1))
3-element Vector{Int64}:
 1
 2
 4
```
