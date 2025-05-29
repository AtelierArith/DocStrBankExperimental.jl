```
ClosedPath(c::AbstractVector; tol=<default>)
ClosedPath(P::Path; tol=<default>)
```

Given a vector `c` of curves, or an existing path, construct a closed path. The path is checked for continuity (to tolerance `tol`) at all of the vertices.
