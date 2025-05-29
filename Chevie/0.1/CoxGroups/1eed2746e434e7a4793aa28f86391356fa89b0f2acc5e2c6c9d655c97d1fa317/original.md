`words(W::CoxeterGroup[,l::Integer])`

With  one argument this works only if `W` is finite; it returns the reduced Coxeter  words  of  elements  of  `W`  by  increasing length. If the second argument  is an integer `l`, only the  elements of length `l` are returned; this works for infinite Coxeter groups.

```julia_repl
julia> W=coxgroup(:G,2)
G₂

julia> e=elements(W,6)
1-element Vector{Perm{Int16}}:
 (1,7)(2,8)(3,9)(4,10)(5,11)(6,12)

julia> e[1]==longest(W)
true
```
