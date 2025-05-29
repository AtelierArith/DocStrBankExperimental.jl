```
Path(c::AbstractVector; tol=<default>)
```

Given a vector `c` of curves, construct a path. The path is checked for continuity (to tolerance `tol`) at the interior vertices.
