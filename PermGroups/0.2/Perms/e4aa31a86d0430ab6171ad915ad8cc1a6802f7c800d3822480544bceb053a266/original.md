`mappingPerm([::Type{T},]a,b)`

given  two lists of positive integers  without repetition `a` and `b`, this function finds a `Perm{T}` `p` such that `a.^p==b`. If omitted `T` is taken to be `Int16`.

```julia-repl
julia> mappingPerm([1,2,5,3],[2,3,4,6])
(1,2,3,6,5,4)
```
