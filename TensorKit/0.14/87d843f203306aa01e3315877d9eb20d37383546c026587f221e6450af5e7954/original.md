```
removeunit(tsrc::AbstractTensorMap, i; copy=false) -> tdst
```

This removes a trivial tensor product factor at position `1 ≤ i ≤ N`, where `i` can be specified as an `Int` or as `Val(i)` for improved type stability. For this to work, that factor has to be isomorphic to the field of scalars.

If `copy=false`, `tdst` might share data with `tsrc` whenever possible. Otherwise, a copy is always made.

This operation undoes the work of [`insertleftunit`](@ref insertleftunit(::AbstractTensorMap, ::Val{i}) where {i})  and [`insertrightunit`](@ref insertrightunit(::AbstractTensorMap, ::Val{i}) where {i}).
