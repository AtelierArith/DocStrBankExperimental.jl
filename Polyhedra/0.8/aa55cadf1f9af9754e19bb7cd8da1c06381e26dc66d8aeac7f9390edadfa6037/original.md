```
removehredundancy!(p::HRep; kws...)
```

Removes the elements of the H-representation of `p` that can be removed without changing the polyhedron represented by `p`. That is, it only keeps the halfspaces corresponding to facets of the polyhedron.

The remaining keyword arguments `kws` are passed to [`detectvlinearity!`](@ref) and [`detecthlinearity!`](@ref).
