`elements(W::CoxeterGroup[,l])`

When  `l` is  not given  this works  only if  `W` is finite; it returns the elements of `W` sorted by increasing Coxeter length. If the second argument is an integer `l`, the elements of `W` of Coxeter length `l` are returned.

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> e=elements(W,6)
1-element Vector{Perm{Int16}}:
 (1,7)(2,8)(3,9)(4,10)(5,11)(6,12)

julia> e[1]==longest(W)
true
```
