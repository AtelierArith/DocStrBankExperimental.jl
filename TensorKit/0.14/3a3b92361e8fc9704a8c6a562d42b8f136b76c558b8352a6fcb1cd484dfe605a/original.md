```
removeunit(P::ProductSpace, i::Int)
```

This removes a trivial tensor product factor at position `1 ≤ i ≤ N`, where `i` can be specified as an `Int` or as `Val(i)` for improved type stability. For this to work, that factor has to be isomorphic to the field of scalars.

This operation undoes the work of [`insertleftunit`](@ref insertleftunit(::ProductSpace, ::Val{i}) where {i})  and [`insertrightunit`](@ref insertrightunit(::ProductSpace, ::Val{i}) where {i}).
