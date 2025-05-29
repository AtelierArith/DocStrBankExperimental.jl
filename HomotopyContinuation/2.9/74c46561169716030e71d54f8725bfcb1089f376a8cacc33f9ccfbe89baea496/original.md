```
search_in_radius(tree::VoronoiTree, v::AbstractVector, tol::Real)
```

Search whether the given `tree` contains a point `p` with distances at most `tol` from `v`. Returns `nothing` if no point exists, otherwise the identifier of `p` is returned.
