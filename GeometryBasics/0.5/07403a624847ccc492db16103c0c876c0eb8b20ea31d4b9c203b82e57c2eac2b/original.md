```
decompose(facetype, contour::AbstractArray{<:Point})
```

Triangulate a Polygon without hole.

Returns a Vector{`facetype`} defining indexes into `contour`.
