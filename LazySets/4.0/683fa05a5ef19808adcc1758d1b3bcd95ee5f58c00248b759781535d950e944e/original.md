# Extended help

```
convex_hull(X::LazySet; kwargs...)
```

### Output

The set `X` itself if its type indicates that it is convex, or a new set with the list of the vertices describing the convex hull.

### Algorithm

For non-convex sets, this method relies on the `vertices_list` method.
