```
OpticUnit(body::Ellipsoid, pointin::Bool, n::Float64, register::Bool, name::String)
```

Convenience function to build optical units. Build an optical unit depending on if the normal should be pointing in or out, `pointin`. The correct AffineMap transformation will be automatically calculated.
