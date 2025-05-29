```
flatten(c::GeometryReference; depth::Integer=-1, name=uniquename("flatten_"*name(structure(c))), metadata_filter=nothing)
```

Return a new structure with name `name` with recursively flattened references and arrays up to a hierarchical `depth`.

Flattening adds the elements of references to the top-level coordinate system with appropriate transformations, then discards those references. Deeper references and arrays are brought upwards and are not discarded. If `depth=0`, a new coordinate system is returned containing only the reference.

`metadata_filter` can be a function that takes a `DeviceLayout.Meta` and returns a `Bool`, like a function returned by [`layer_inclusion`](@ref). In that case, only elements whose metadata `m` have `metadata_filter(m) == true` will be retained while flattening. Elements of deeper references and arrays are not filtered.

The reference `c` remains unmodified.
