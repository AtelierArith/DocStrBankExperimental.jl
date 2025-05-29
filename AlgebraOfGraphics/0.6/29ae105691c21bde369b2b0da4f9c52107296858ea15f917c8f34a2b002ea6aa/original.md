```
draw(p::PaginatedLayers; kws...)
```

Draw each element of `PaginatedLayers` `p` and return a `Vector{FigureGrid}`. Keywords `kws` are passed to the underlying `draw` calls.
