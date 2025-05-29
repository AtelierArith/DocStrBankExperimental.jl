```
flatten!(c::AbstractCoordinateSystem, depth::Integer=-1, metadata_filter=nothing, max_copy=Inf)
```

Recursively flatten references and arrays up to a hierarchical `depth`, adding their elements to `c` with appropriate transformations.

The references and arrays that were flattened are then discarded. Deeper references and arrays are brought upwards and are not discarded.

This function has no effect for `depth == 0`, and unlimited depth by default.
