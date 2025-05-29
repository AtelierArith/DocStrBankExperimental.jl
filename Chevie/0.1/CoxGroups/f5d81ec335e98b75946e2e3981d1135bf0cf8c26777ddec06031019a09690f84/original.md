`isleftdescent(W::CoxeterGroup,w,i::Integer)`

returns  `true` iff the  `i`-th generating reflection  of the Coxeter group `W`  is in  the left  descent set  of the  element `w`  of `W`, that is iff `length(W,W(i)*w)<length(W,w)`.

```julia-repl
julia> W=coxsym(3)
𝔖 ₃

julia> isleftdescent(W,Perm(1,2),1)
true
```
