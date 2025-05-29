An intertype expression representing a type.

TODO: Generic types TODO: Remove anonymous sums, anonymous products TODO: Separate out primitives, so that this is something like

```julia
@data InterType begin
  PrimType(prim::InterTypePrimitive)
  TypeRef(path::RefPath)
  TypeApp(type::InterType, args::Vector{InterType})
end
```
