```
insertleftunit(P::ProductSpace, i::Int=length(P) + 1; conj=false, dual=false)
```

Insert a trivial vector space, isomorphic to the underlying field, at position `i`, which can be specified as an `Int` or as `Val(i)` for improved type stability. More specifically, adds a left monoidal unit or its dual.

See also [`insertrightunit`](@ref insertrightunit(::ProductSpace, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::ProductSpace, ::Val{i}) where {i}).
