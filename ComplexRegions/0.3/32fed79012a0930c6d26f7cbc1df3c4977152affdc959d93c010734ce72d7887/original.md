```
Polygon(p::AbstractPath; tol=<default>)
Polygon(p::AbstractVector{<:AbstractCurve}; tol=<default>)
```

Construct a polygon from a (possibly closed) path, or from a vector of curves. The `tol` parameter is a tolerance used when checking continuity and closedness of the path.
