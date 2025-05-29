```
pathtopolys(f::Paths.Segment{T}, s::Paths.Style; kwargs...)
```

Given a path node represented with a segment and style, construct an equivalent set of polygons. For some linear segments and styles, a set of `Polygon{T}` is sufficient, for others such as curves then `CurvilinearRegion{T}` is necessary.

This is particularly helpful if a Path is being used within the construction of a component rather than as part of the SchematicGraph.
