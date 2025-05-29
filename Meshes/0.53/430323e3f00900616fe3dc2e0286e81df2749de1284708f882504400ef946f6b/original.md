```
PolyArea(outer)
PolyArea([outer, inner₁, inner₂, ..., innerₖ])
```

A polygonal area with `outer` ring, and optional inner rings `inner₁`, `inner₂`, ..., `innerₖ`.

Rings can be a vector of [`Point`](@ref) or a vector of tuples with coordinates for convenience, in which case the first point should *not* be repeated at the end of the vector.
