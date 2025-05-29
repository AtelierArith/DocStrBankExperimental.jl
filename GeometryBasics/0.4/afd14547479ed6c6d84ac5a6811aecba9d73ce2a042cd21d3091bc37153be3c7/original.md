```
decompose(facetype, contour::AbstractArray{<:AbstractPoint})
```

Triangulate a Polygon without hole.

Returns a Vector{`facetype`} defining indexes into `contour`.
