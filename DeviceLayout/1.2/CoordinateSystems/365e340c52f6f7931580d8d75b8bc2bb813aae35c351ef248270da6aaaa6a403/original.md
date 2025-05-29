```
flatten(c::GeometryStructure; depth::Integer=-1, name=uniquename("flatten_"*name(c)))
```

Return a new coordinate system with name `name` with recursively flattened references and arrays up to a hierarchical `depth`.

Flattening a `CoordinateSystem` or `Cell` produces a coordinate system of the same type (meaning these can also be flattened in-place with [`flatten!`](@ref)), while flattening other structures generally produces a `CoordinateSystem` with the same coordinate type.

Flattening adds the elements of references to the top-level structure with appropriate transformations, then discards those references. Deeper references and arrays are brought upwards and are not discarded.

This function has no effect on references for `depth == 0`, and unlimited depth by default.
