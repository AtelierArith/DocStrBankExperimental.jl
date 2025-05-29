```
edgeplot(paths::Vector{AbstractPath})
edgeplot!(sc, paths::Vector{AbstractPath})
```

Recipe to draw the edges. Attribute `plottype` can be either. If `eltype(pathes) <: Line` draw using `linesegments`. If `<:AbstractPath` draw using bezier segments. All attributes are passed down to the actual recipe.
