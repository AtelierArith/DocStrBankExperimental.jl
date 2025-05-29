```
insertrightunit(P::ProductSpace, i=lenght(P); conj=false, dual=false)
```

Insert a trivial vector space, isomorphic to the underlying field, after position `i`, which can be specified as an `Int` or as `Val(i)` for improved type stability. More specifically, adds a right monoidal unit or its dual.

See also [`insertleftunit`](@ref insertleftunit(::ProductSpace, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::ProductSpace, ::Val{i}) where {i}).
