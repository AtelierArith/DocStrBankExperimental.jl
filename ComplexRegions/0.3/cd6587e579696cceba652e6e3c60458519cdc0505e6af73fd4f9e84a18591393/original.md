```
CircularPolygon(p::AbstractPath; tol=<default>)
CircularPolygon(p::AbstractVector; tol=<default>)
```

Construct a circular polygon from a (possibly closed) path, or from a vector of curves. The `tol` parameter is a tolerance used when checking continuity and closedness of the path.
