```
enable_index_translation()
```

Enables the translation of summation indices over occupied and virtual to be printed as ijkl... and abcd... respectively instead of pqrs...

By default translated indices lose their subspace coloring to reduce redundant information (unless the index is in an even stricter subspace which requires coloring nevertheless). To re-enable the coloring see [`enable_color_translated`](@ref).

This is enabled by default.
