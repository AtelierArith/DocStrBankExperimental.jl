`leftdescents(W,w)`

The  left descents of the element `w` of the Coxeter group `W`, that is the set of `i` such that `length(W,W(i)*w)<length(W,w)`.

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> leftdescents(W,Perm(1,3))
2-element Vector{Int64}:
 1
 2
```
