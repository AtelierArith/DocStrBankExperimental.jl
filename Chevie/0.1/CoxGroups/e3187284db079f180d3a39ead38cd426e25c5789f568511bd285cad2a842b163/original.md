`firstleftdescent(W,w)`

returns the index in `gens(W)` of the first element of the left descent set of  `w` –- that is, the first  `i` such that if `s=W(i)` then `l(sw)<l(w). It returns`nothing`for`one(W)`.

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> firstleftdescent(W,Perm(2,3))
2
```
