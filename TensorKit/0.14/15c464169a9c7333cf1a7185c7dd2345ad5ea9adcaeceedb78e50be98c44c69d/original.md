```
insertrightunit(tsrc::AbstractTensorMap, i=numind(t);
                conj=false, dual=false, copy=false) -> tdst
```

Insert a trivial vector space, isomorphic to the underlying field, after position `i`, which can be specified as an `Int` or as `Val(i)` for improved type stability. More specifically, adds a right monoidal unit or its dual.

If `copy=false`, `tdst` might share data with `tsrc` whenever possible. Otherwise, a copy is always made.

See also [`insertleftunit`](@ref insertleftunit(::AbstractTensorMap, ::Val{i}) where {i}), [`removeunit`](@ref removeunit(::AbstractTensorMap, ::Val{i}) where {i}).
