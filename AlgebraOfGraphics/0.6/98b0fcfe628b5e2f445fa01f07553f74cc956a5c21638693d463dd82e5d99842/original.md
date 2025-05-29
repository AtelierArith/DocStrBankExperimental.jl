```
draw(p::PaginatedLayers, i::Int; kws...)
```

Draw the ith element of `PaginatedLayers` `p` and return a `FigureGrid`. Keywords `kws` are passed to the underlying `draw` call.

You can retrieve the number of elements using `length(p)`.
