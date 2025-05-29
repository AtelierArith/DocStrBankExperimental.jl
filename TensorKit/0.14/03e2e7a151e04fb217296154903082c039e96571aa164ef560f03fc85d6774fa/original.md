```
removeunit(P::HomSpace, i)
```

This removes a trivial tensor product factor at position `1 ≤ i ≤ N`, where `i` can be specified as an `Int` or as `Val(i)` for improved type stability. For this to work, the space at position `i` has to be isomorphic to the field of scalars.

This operation undoes the work of [`insertleftunit`](@ref insertleftunit(::HomSpace, ::Val{i}) where {i})  and [`insertrightunit`](@ref insertrightunit(::HomSpace, ::Val{i}) where {i}).
