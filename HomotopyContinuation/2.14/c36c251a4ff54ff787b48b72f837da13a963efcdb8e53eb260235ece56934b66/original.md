```
add!(tree::VoronoiTree, v, id, tol)
```

Insert in the tree the point `v` with identifier `id` if `search_in_radius(tree v, tol)` is `nothing`. If this is the case the tuple `(id, true)` is returned, otherwise the obtained identifier and `false` is returned.
